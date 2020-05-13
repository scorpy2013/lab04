## Laboratory work IV

<a href="https://yandex.ru/efir/?stream_id=vCgeA9EiySzw"><img src="https://raw.githubusercontent.com/tp-labs/lab04/master/preview.png" width="640"/></a>

Данная лабораторная работа посвещена изучению систем непрерывной интеграции на примере сервиса **Travis CI**

```sh
$ open https://travis-ci.org
```

## Tasks

- [x] 1. Авторизоваться на сервисе **Travis CI** с использованием **GitHub** аккаунта
- [x] 2. Создать публичный репозиторий с названием **lab04** на сервисе **GitHub**
- [x] 3. Ознакомиться со ссылками учебного материала
- [x] 4. Включить интеграцию сервиса **Travis CI** с созданным репозиторием
- [x] 5. Получить токен для **Travis CLI** с правами **repo** и **user**
- [x] 6. Получить фрагмент вставки значка сервиса **Travis CI** в формате **Markdown**
- [x] 7. Выполнить инструкцию учебного материала
- [x] 8. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial
$ git clone https://github.com/scorpy2013/lab04.git
Cloning into 'lab04'...
remote: Enumerating objects: 87, done.
remote: Counting objects: 100% (87/87), done.
remote: Compressing objects: 100% (61/61), done.
remote: Total 87 (delta 27), reused 81 (delta 25), pack-reused 0
Receiving objects: 100% (87/87), 2.11 MiB | 1.95 MiB/s, done.
Resolving deltas: 100% (27/27), done.

```sh
$ export GITHUB_USERNAME=scorpy2013
$ export GITHUB_TOKEN=0dc94d9c9fe7556bc832fbc82e5b22c21b58328c
```

```sh
$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
~/Documents/GitHub/scorpy2013/lab04/scorpy2013/workspace ~/Documents/GitHub/scorpy2013/lab04/scorpy2013/workspace
$ source scripts/activate
```

```sh
$ \curl -sSL https://get.rvm.io | bash -s -- --ignore-dotfiles
Turning on ignore dotfiles mode.
Downloading https://github.com/rvm/rvm/archive/master.tar.gz
tar: bin/ruby-rvm-env: Cannot create symlink to ‘rvm-shell’: No such file or directory
tar: install: Cannot create symlink to ‘scripts/install’: No such file or directory
tar: scripts/functions/requirements/omnios: Cannot create symlink to ‘openindiana’: No such file or directory
tar: Exiting with failure status due to previous errors
Could not extract RVM sources.
Downloading https://bitbucket.org/mpapis/rvm/get/master.tar.gz
Installing RVM to /c/Users/User/.rvm/
Installation of RVM in /c/Users/User/.rvm/ is almost complete:

  * To start using RVM you need to run `source /c/Users/User/.rvm/scripts/rvm`
    in all your open shell windows, in rare cases you need to reopen all shell windows.
Do not know how to check user shell on 'MINGW64_NT-6.1-7601'.
Thanks for installing RVM 🙏
Please consider donating to our open collective to help us maintain RVM.

👉  Donate: https://opencollective.com/rvm/donate
$ echo "source $HOME/.rvm/scripts/rvm" >> scripts/activate
$ . scripts/activate
$ rvm autolibs disable
$ rvm install ruby-2.4.2
Searching for binary rubies, this might take some time.
No binary rubies available for: kali/kali-rolling/x86_64/ruby-2.6.3.
Continuing with compilation. Please read 'rvm help mount' to get more information on binary rubies.
Installing Ruby from source to: /home/scorpy/.rvm/rubies/ruby-2.6.3, this may take a while depending on your cpu(s)...
ruby-2.6.3 - #downloading ruby-2.6.3, this may take a while depending on your connection...
ruby-2.6.3 - #extracting ruby-2.6.3 to /home/scorpy/.rvm/src/ruby-2.6.3.....
ruby-2.6.3 - #configuring.......................................................................
ruby-2.6.3 - #post-configuration..
ruby-2.6.3 - #compiling..........................................................................................
ruby-2.6.3 - #installing..................
ruby-2.6.3 - #making binaries executable..
Rubygems 3.0.3 already available in installed ruby, skipping installation, use --force to reinstall.
ruby-2.6.3 - #gemset created /home/scorpy/.rvm/gems/ruby-2.6.3@global
ruby-2.6.3 - #importing gemset /home/scorpy/.rvm/gemsets/global.gems..................there was an error installing gem gem-wrappers
..................there was an error installing gem rubygems-bundler
........................there was an error installing gem rvm
.......
ruby-2.6.3 - #generating global wrappers.................
Error running 'run_gem_wrappers regenerate',
please read /home/scorpy/.rvm/log/1558774975_ruby-2.6.3/gemset.wrappers.global.log
ruby-2.6.3 - #gemset created /home/scorpy/.rvm/gems/ruby-2.6.3
ruby-2.6.3 - #importing gemsetfile /home/scorpy/.rvm/gemsets/default.gems evaluated to empty gem list
ruby-2.6.3 - #generating default wrappers.................
Error running 'run_gem_wrappers regenerate',
please read /home/scorpy/.rvm/log/1558774975_ruby-2.6.3/gemset.wrappers.default.log
ruby-2.6.3 - #adjusting #shebangs for (gem irb erb ri rdoc testrb rake).
Install of ruby-2.6.3 - #complete 
Ruby was built without documentation, to build it run: rvm docs generate-ri
$ rvm use 2.4.2 --default               # Установка основной установленной версии 
$ gem install travis                    # Установка travis 

Fetching: faraday_middleware-0.13.1.gem (100%)
Successfully installed faraday_middleware-0.13.1
Fetching: highline-1.7.10.gem (100%)
Successfully installed highline-1.7.10
Fetching: backports-3.14.0.gem (100%)
Successfully installed backports-3.14.0
Fetching: addressable-2.4.0.gem (100%)
Successfully installed addressable-2.4.0
Fetching: net-http-pipeline-1.0.1.gem (100%)
Successfully installed net-http-pipeline-1.0.1
Fetching: gh-0.15.1.gem (100%)
Successfully installed gh-0.15.1
Fetching: launchy-2.4.3.gem (100%)
Successfully installed launchy-2.4.3
Fetching: typhoeus-0.8.0.gem (100%)
Successfully installed typhoeus-0.8.0
Fetching: websocket-1.2.8.gem (100%)
Successfully installed websocket-1.2.8
Fetching: pusher-client-0.6.2.gem (100%)
Successfully installed pusher-client-0.6.2
Fetching: travis-1.8.10.gem (100%)
Successfully installed travis-1.8.10
Parsing documentation for faraday_middleware-0.13.1
Installing ri documentation for faraday_middleware-0.13.1
Parsing documentation for highline-1.7.10
Installing ri documentation for highline-1.7.10
Parsing documentation for backports-3.14.0
Installing ri documentation for backports-3.14.0
Parsing documentation for addressable-2.4.0
Installing ri documentation for addressable-2.4.0
Parsing documentation for net-http-pipeline-1.0.1
Installing ri documentation for net-http-pipeline-1.0.1
Parsing documentation for gh-0.15.1
Installing ri documentation for gh-0.15.1
Parsing documentation for launchy-2.4.3
Installing ri documentation for launchy-2.4.3
Parsing documentation for typhoeus-0.8.0
Installing ri documentation for typhoeus-0.8.0
Parsing documentation for websocket-1.2.8
Installing ri documentation for websocket-1.2.8
Parsing documentation for pusher-client-0.6.2
Installing ri documentation for pusher-client-0.6.2
Parsing documentation for travis-1.8.10
Installing ri documentation for travis-1.8.10
Done installing documentation for faraday_middleware, highline, backports, addressable, net-http-pipeline, gh, launchy, typhoeus, websocket, pusher-client, travis after 7 seconds
11 gems installed
```

```sh
$ git clone https://github.com/${GITHUB_USERNAME}/lab03 projects/lab04
Cloning into 'projects/lab04'...
remote: Enumerating objects: 91, done.
remote: Counting objects: 100% (91/91), done.
remote: Compressing objects: 100% (48/48), done.
Receiving objects:  51% (47/91), 984.00 KiB | 1.91 MiB/s
Receiving objects: 100% (91/91), 1.02 MiB | 1.78 MiB/s, done.
Resolving deltas: 100% (42/42), done.
$ cd projects/lab04
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab04
```

```sh
$ cat > .travis.yml <<EOF
language: cpp
EOF
```

```sh
$ cat >> .travis.yml <<EOF

script:
- cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
- cmake --build _build
- cmake --build _build --target install
EOF
```

```sh
$ cat >> .travis.yml <<EOF

addons:
  apt:
    sources:
      - george-edison55-precise-backports
    packages:
      - cmake
      - cmake-data
EOF
```

```sh
$ travis login --github-token ${GITHUB_TOKEN}
```

```sh
$ travis lint
```

```sh
$ ex -sc '1i|<фрагмент_вставки_значка>' -cx README.md
```

```sh
$ git add .travis.yml
warning: LF will be replaced by CRLF in .travis.yml.
The file will have its original line endings in your working directory
$ git add README.md
$ git commit -m"added CI"

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'User@User-PC.(none)')
$ git push origin master
To https://github.com/scorpy2013/lab04
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'https://github.com/scorpy2013/lab04'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

```sh
$ travis lint
Warnings for .travis.yml:
[x] value for addons section is empty, dropping
[x] in addons section: unexpected key apt, dropping
$ travis accounts
scorpy2013 (scorpy2013): subscribed, 16 repositories
$ travis sync
synchronizing: .. done
$ travis repos

scorpy2013/lab04 (active: yes, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab02 (active: no, admin: yes, push: yes, pull: yes)
Description: Изучение систем контроля версий на примере Git

scorpy2013/lab09 (active: no, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab08 (active: no, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab07 (active: no, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab06 (active: no, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab05 (active: yes, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab01 (active: no, admin: yes, push: yes, pull: yes)
Description: Изучение утилит для разработки проектов

scorpy2013/lab03 (active: yes, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/Homework (active: no, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/Test-Repos (active: yes, admin: yes, push: yes, pull: yes)
Description: ???

scorpy2013/lab00-1 (active: no, admin: no, push: yes, pull: yes)
Description: Изучение систем обмена данными

scorpy2013/lab-00-scorpy2013-1 (active: no, admin: yes, push: yes, pull: yes)
Description: lab-00-scorpy2013 created by GitHub Classroom

scorpy2013/lab-00-scorpy2013 (active: yes, admin: yes, push: yes, pull: yes)
Description: It is my first repository.

scorpy2013/hello-world (active: no, admin: yes, push: yes, pull: yes)
Description: My first practise

scorpy2013/lab-00-levon-avackimyanc (active: no, admin: yes, push: yes, pull: yes)
Description: lab-00-levon-avackimyanc created by GitHub Classroom

$ travis enable
Detected repository as scorpy2013/lab04, is this correct? |yes| yes
scorpy2013/lab04: enabled :)
$ travis whatsup
scorpy2013/lab04 passed: #1
$ travis branches
master:  #1    passed     added CI
$ travis history
#1 passed:       master added CI
$ travis show
Job #1.1:  added CI
State:         passed
Type:          push
Branch:        master
Compare URL:   https://github.com/scorpy2013/lab04/compare/
Duration:      52 sec
Started:       2020-05-13 12:20:53
Finished:      2020-05-13 12:21:45
Allow Failure: false
Config:        os: linux
```

## Report

```sh
$ popd
$ export LAB_NUMBER=04
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
Cloning into 'tasks/lab04'...
remote: Enumerating objects: 15, done.
remote: Counting objects: 100% (15/15), done.
remote: Compressing objects: 100% (14/14), done.
Receiving objects: 100% (81/81), 2.11 MiB | 2.12 MiB/s, done.6R

Resolving deltas: 100% (23/23), done.
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```

## Homework

Вы продолжаете проходить стажировку в "Formatter Inc." (см [подробности](https://github.com/tp-labs/lab03#Homework)).

В прошлый раз ваше задание заключалось в настройке автоматизированной системы **CMake**.

Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в [прошлый раз](https://github.com/tp-labs/lab03#Homework). Настройте сборочные процедуры на различных платформах:
* используйте [TravisCI](https://travis-ci.com/) для сборки на операционной системе **Linux** с использованием компиляторов **gcc** и **clang**;
* используйте [AppVeyor](https://www.appveyor.com/) для сборки на операционной системе **Windows**.

## Links

- [Travis Client](https://github.com/travis-ci/travis.rb)
- [AppVeyour](https://www.appveyor.com/)
- [GitLab CI](https://about.gitlab.com/gitlab-ci/)

```
Copyright (c) 2015-2020 The ISC Authors
```
