---
title: "No panels, icons etc. with FreeNX / NXSERVER. Plain deskto only"
date: 2009-04-06
forum: Desktop Environments
---

### Post by EyeScreaMan on 2009-04-06
Hi. 

I have an issue with **FreeNX** / **NXSERVER**.

**I am using Ubuntu 9.04 (Jaunty Jackalope) Beta**

Tried both - FreeNX and NX Server from NoMachine.

> 
rc  freenx-server                              0.7.3+teambzr102-0freenxteam1     Remote desktop/application/thin-client serve
ii  freenx-session-launcher                    0.7.3+teambzr102-0freenxteam1     Remote desktop/application/thin-client serve
ii  libxcomp3                                  3.3.0-3-0ubuntu1                  NX X compression library
ii  libxcompext3                               1:3.3.0-3-0ubuntu1                NX X11 protocol compression extensions libra
ii  libxcompshad3                              3.3.0-3-0freenxteam1              NX shadowing library
ii  nxagent                                    1:3.3.0-5-0ubuntu1                X server for remote access
ii  nxclient                                   3.3.0-6                           NX Client
ii  nxlibs                                     1:3.3.0-5-0ubuntu1                NX support libraries
ii  nxnode                                     3.3.0-17                          NX Server Node
ii  nxserver                                   3.3.0-22                          NX Server


I have no problems connecting, but after loging in, all i can do is operate on plain desktop with right mouse context menu.
I see no panels, no icons, only wallpaper.

[SIZE="3"]Screenshot[/SIZE]:
[[IMG]http://www.cubeupload.com/files/thumbs/th.161a00untitled.jpg[/IMG]](http://www.cubeupload.com/img/161a00untitled.jpg)

```

Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: initialization: starting parse of config file '/usr/NX/etc/node.cfg' Logger::log nxserver 1118
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: saved env 'DISPLAY'='localhost:12.0' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: setting env 'DISPLAY'= '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: trying to run command '/bin/bash --login -c /bin/hostname' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals are now blocked ... Logger::log nxserver 2443
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11786]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command is running with pid: 11786 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: closed command STDIN '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: added command STDOUT to list of selector set '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: added command STDERR to selector set '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11786' stderr was closed. '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11786' stdout was closed. '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11786' finished with: 0 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11786' stdout was 'pajonk\n' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11786' stderr was '' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: env DISPLAY reset to 'localhost:12.0' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: disabling logging for package 'NXMsg' 'Logger::disablePackage'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: disabling logging for package 'NXLogin' 'Logger::disablePackage'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: disabling logging for package 'InfoManager' 'Logger::disablePackage'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'welcome' '' 'NXShell::handle_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'hello' 'NXCLIENT - Version 3.3.0' 'NXShell::get_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'hello' 'NXCLIENT - Version 3.3.0' 'NXShell::handle_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: SCRIPTS:: script_before_login [83.8.238.166] 'NXScripts::script_before_login'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'set' 'SHELL_MODE SHELL' 'NXShell::get_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'set' 'SHELL_MODE SHELL' 'NXShell::handle_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'set' 'AUTH_MODE PASSWORD' 'NXShell::get_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'set' 'AUTH_MODE PASSWORD' 'NXShell::handle_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'login' '' 'NXShell::get_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'login' '' 'NXShell::handle_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Local IP determined from SSH_CONNECTION: 83.8.238.166 4780 10.0.0.10 6122 'NXClientConnection::getLocalIp'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/guests.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: redirecting stderr to file '/dev/null' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run_command: stdin will be not redirect '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run_command: stdout will be not redirect '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: trying to run command 'stty -echo' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals are now blocked ... Logger::log nxserver 2443
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11787]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: closed STDERR redirected file '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command is running with pid: 11787 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command STDIN will be not closed '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: not added command STDOUT to list of selector set: pipe was not created '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: not added command STDERR to list of selector set: redirected to a file '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11787' finished with: 1 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11787' stdout was '' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11787' stderr was '' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: redirecting stderr to file '/dev/null' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run_command: stdin will be not redirect '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run_command: stdout will be not redirect '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: trying to run command 'stty echo' '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals are now blocked ... Logger::log nxserver 2443
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11788]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: closed STDERR redirected file '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command is running with pid: 11788 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command STDIN will be not closed '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: not added command STDOUT to list of selector set: pipe was not created '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: not added command STDERR to list of selector set: redirected to a file '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11788' finished with: 1 '(eval)'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11788' stdout was '' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11788' stderr was '' 'main::run_command'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: user login is foo (NXShell). Stored status. 'Logger::statusPush'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: user password is '******' (NXShell). Stored status. 'Logger::statusPush'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: using 'sshd authentication' (NXShell). Stored status. 'Logger::statusPush'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: checking user 'foo@127.0.0.1:6122' credentials 'NXNssUserManager::auth'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: executing command: '/usr/NX/bin/nxssh -nxauthonly -o 'StrictHostKeyChecking no' -l foo 127.0.0.1 -p 6122 -2' 'NXNssUserManager::auth'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: nxssh pid is: 11789 'NXNssUserManager::auth'
Apr  6 13:23:28 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: printing password to nxssh stdin: ******** '(eval)'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in stdout channel: 'NX> 205 foo@127.0.0.1's password: \n' '(eval)'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in stdout channel: 'NX> 206 ssh-userauth2 successful: method password\n' '(eval)'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: stderr was closed '(eval)'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: stdout channel was closed '(eval)'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: waiting process: with pid '11789' 'WaitProcess::waitProcess'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: waiting process: using 5s as timeout 'WaitProcess::waitProcess'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: process with pid '11789' has exited 'WaitProcess::waitProcess'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: process exit status is '0' 'WaitProcess::getExitStatus'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: User 'foo' logged in from '83.8.238.166'. 'NXLogin::set'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/users.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: SCRIPTS:: script_after_login [foo] 'NXScripts::script_after_login'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'listsession' '--user="foo" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"' 'NXShell::get_command'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'listsession' '--user="foo" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"' 'NXShell::handle_command'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getLastParameters: command parameters '--user="foo" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"'. NXShell::getLastParameters handlers/nxserver 4763
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter string is '--user="foo" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"'. 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--user=foo'. 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--status=suspended,running'. 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--geometry=1920x1200x32+render'. 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--type=unix-gnome'. 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: command parameters '--user="foo" --status="suspended,running" --geometry="1920x1200x32+render" --type="unix-gnome"' 'NXShell::getParameters'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:29 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: no pids to wait 'main::__run_command_waitpid'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'startsession' '--link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="pajonk" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102/pl" --screeninfo="1280x1024x32+render"' 'NXShell::get_command'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'startsession' '--link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="pajonk" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102/pl" --screeninfo="1280x1024x32+render"' 'NXShell::handle_command'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getLastParameters: command parameters '--link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="pajonk" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102/pl" --screeninfo="1280x1024x32+render"'. NXShell::getLastParameters handlers/nxserver 2122
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter string is '--link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="pajonk" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102/pl" --screeninfo="1280x1024x32+render"'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--link=lan'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--backingstore=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--encryption=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--cache=16M'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--images=64M'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--shmem=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--shpix=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--strict=0'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--composite=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--media=0'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--imagecompressionmethod=3'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--imagecompressionlevel=-1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--render=1'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--session=pajonk'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--type=unix-gnome'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--geometry=1280x1024'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: NX client operating system is winnt. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--client=winnt'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--keyboard=pc102/pl'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: getParameters: parameter '--screeninfo=1280x1024x32+render'. 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: command parameters '--link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="pajonk" --type="unix-gnome" --geometry="1280x1024" --client="winnt" --keyboard="pc102/pl" --screeninfo="1280x1024x32+render"' 'NXShell::getParameters'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: User profiles are disabled. Skipping check of item: server-clipboard into profiles 'NXProfilesManager::check_item_permission'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: User profiles are disabled. Skipping check of item: client-clipboard into profiles 'NXProfilesManager::check_item_permission'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Enabling persistent sessions for all users 'NXShell::handler_session_start'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Enable load balancing: 0 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Available host list: localhost:6122 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Selected node host no: 1 of: 1 available host 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Configured node host list: localhost:6122 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 4 'main::lockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 4 main::unLockFile nxserver 3198
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: User profiles are disabled. Skipping check of item: localhost/6122 into profiles 'NXProfilesManager::check_item_permission'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Checking host: localhost for user:foo (checking response:localhost) 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: Selected node host:localhost with port:6122 'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Checking running nodes: localhost:6122 'main::checkNodeIsEnabledDisabled'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Found nodes: localhost:6122 in status: running 'main::checkNodeIsEnabledDisabled'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: Current selected node: localhost is in status: running  'main::selectNode'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: user's sessions are: 0 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: local sessions has: 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: searching for next display to use from num. '1000', to num. '1199' 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: last used display num. is '1014' 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: search will stop to display num. '1014' 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: checking resources of display num. '1015' 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: check display resources passed for display '1015' 'NXSession2::chkDisplayResources2'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: found free display: '1015' 'NXSession2::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 4 'main::lockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 4 main::unLockFile nxserver 3198
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: User profiles are disabled. Skipping check of item: unix-gnome into profiles 'NXProfilesManager::check_item_permission'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: Selected session type: unix-gnome allowed in the profile of user: foo 'NXShell::Static'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: trying to run command 'ps -e' '(eval)'
Apr  6 13:23:31 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals are now blocked ... Logger::log nxserver 2443
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11890]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: command is running with pid: 11890 '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: closed command STDIN '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: added command STDOUT to list of selector set '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: added command STDERR to selector set '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11890' stderr was closed. '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11890' stdout was closed. '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11890' finished with: 0 '(eval)'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11890' stdout was '  PID TTY          TIME CMD\n    1 ?        00:00:01 init\n    2 ?        00:00:00 kthreadd\n    3 ?        00:00:00 migration/0\n    4 ?        00:00:00 ksoftirqd/0\n    5 ?        00:00:00 watchdog/0\n    6 ?        00:00:00 events/0\n    7 ?        00:00:00 khelper\n    8 ?        00:00:00 kstop/0\n    9 ?        00:00:00 kintegrityd/0\n   10 ?        00:00:00 kblockd/0\n   11 ?        00:00:00 kacpid\n   12 ?        00:00:00 kacpi_notify\n   13 ?        00:00:00 cqueue\n   14 ?        00:00:07 ata/0\n   15 ?        00:00:00 ata_aux\n   16 ?        00:00:00 ksuspend_usbd\n   17 ?        00:00:00 khubd\n   18 ?        00:00:00 kseriod\n   19 ?        00:00:00 kmmcd\n   20 ?        00:00:00 btaddconn\n   21 ?        00:00:00 btdelconn\n   22 ?        00:00:00 pdflush\n   23 ?        00:00:00 pdflush\n   24 ?        00:00:02 kswapd0\n   25 ?        00:00:00 aio/0\n   26 ?        00:00:00 ecryptfs-kthrea\n   29 ?   
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: process '11890' stderr was '' 'main::run_command'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: inserting session sessionId:D44A1DA85B1C65C953D35AD9DF7BAA04 on 'running' DB 'NXSession2::insertSession'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Node is on localhost, connection will be unencrypted 'main::checkNodeMode'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locking file /usr/NX/etc/administrators.db.lock with bits 1 and timeout 60 main::lockFile nxserver 3187
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Locked. Immediately flock file. fileno: 3 'main::lockFile'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocking file... fileno: 3 main::unLockFile nxserver 3198
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Unlocked 'main::unLockFile'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1005 'NXNodeExec::onMessage'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1006 'NXNodeExec::onMessage'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1008 'NXNodeExec::onMessage'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1009 'NXNodeExec::onMessage'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Registered handler function: 'NXShell::nxsessionSetStatus' for message or event no: 1010 'NXNodeExec::onMessage'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: SCRIPTS:: script_before_start_session [D44A1DA85B1C65C953D35AD9DF7BAA04,foo,localhost,6122] 'NXScripts::script_before_start_session'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: selected user 'foo' is authenticated (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: password for selected user is in 'text' mode (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: preferred auth method is '' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: selected NX Node with host name 'localhost', port '6122' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: selected publickey method to login NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: nxssh command line is '/usr/NX/bin/nxssh -nxservermode -l foo localhost -p 6122 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o 'PubkeyAuthentication yes' -o 'RSAAuthentication yes' -o 'RhostsAuthentication no' -o 'PasswordAuthentication no' -o 'RhostsRSAAuthentication no' -o 'StrictHostKeyChecking no' /usr/NX/bin/nxnode' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals are now blocked ... Logger::log nxserver 2443
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11891]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Signals unblocked Logger::log nxserver 2465
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: nxssh child pid is: 11891 (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: run command: added pid 11891 to the child set. Now pids to wait are: 11891 'main::__add_process_to_wait'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 1000 NXNODE - Version 3.3.0-17 \n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received message 'CONNECTED' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: sent request for service 'startsession' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:32 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: sent parameters 'user=foo&userip=83%2e8%2e238%2e166&uniqueid=D44A1DA85B1C65C953D35AD9DF7BAA04&display=1015&node_number=0&server_name=pajonk&license=%28None%29&subscriptionid=None&productid=LFE&reconnect=1&balance_host=10%2e0%2e0%2e10&encryption_mode=3&connection=local&images=64M&cache=16M&client=winnt&media=0&backingstore=1&encryption=1&strict=0&clipboard=both&imagecompressionlevel=%2d1&imagecompressionmethod=3&shpix=1&rootless=0&composite=1&session=pajonk&shmem=1&type=unix%2dgnome&virtualdesktop=1&render=1&screeninfo=1280x1024x32%2brender&keyboard=pc102%2fpl&geometry=1280x1024&link=lan' to NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 700 Session id: pajonk-1015-D44A1DA85B1C65C953D35AD9DF7BAA04\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '700' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 705 Session display: 1015\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '705' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 703 Session type: unix-gnome\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '703' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 701 Proxy cookie: 0F98DBD35378B407347A4AFDFF26B239\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '701' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 702 Proxy IP: 10.0.0.10\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '702' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 706 Agent cookie: 0F98DBD35378B407347A4AFDFF26B239\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '706' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 704 Session cache: unix-gnome\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '704' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 728 Session caption: NX - foo@pajonk:1015 - pajonk\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 707 SSL tunneling: 1\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '707' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 708 Subscription: LFE/None/LFEN/None\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '708' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 710 Session status: running\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: No registered handler function for message: '710' 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received data in out channel from NX Node: 'NX> 1007 Commit and close FH\n' (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received message 'COMMIT2' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11970]: DEBUG: run command: cleared child set 'main::__reset_process_to_wait'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11970]: DEBUG: waiting for message 'BYE' from NX Node (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11970]: DEBUG: Calling handler function: 'NXUtmp::add' for 'connected to nxnode' event 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11970]: DEBUG: NXutmp logging disabled. 'NXUtmp::add'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11970]: DEBUG: Handler function finished 'NXNodeExec::__onMessageRun'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: returning to interactive mode (NXNodeExec). Stored status. 'Logger::statusPush'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: Session 'D44A1DA85B1C65C953D35AD9DF7BAA04' started by user 'foo'. 'NXShell::handler_session_start'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Server pid for session 'D44A1DA85B1C65C953D35AD9DF7BAA04' is: 11970 'NXShell::handler_session_start'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: SCRIPTS:: script_after_start_session [D44A1DA85B1C65C953D35AD9DF7BAA04,foo,localhost,6122] 'NXScripts::script_after_start_session'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: received command 'bye' '' 'NXShell::get_command'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: handling command 'bye' '' 'NXShell::handle_command'
Apr  6 13:23:34 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: Running nxssh for forwarding session 'NXShell::handler_bye'
Apr  6 13:23:35 pajonk NXSERVER-3.3.0-22[11972]: DEBUG: run command: cleared child set 'main::__reset_process_to_wait'
Apr  6 13:23:35 pajonk NXSERVER-3.3.0-22[11972]: DEBUG: nxssh command: /usr/NX/bin/nxssh -B -E '(eval)'
Apr  6 13:23:35 pajonk NXSERVER-3.3.0-22[11783]: DEBUG: nxssh is now running with pid: 11972 'NXShell::handler_bye' 

```

Thanks for any help!

Best regards ):P

---

### Post by rdoolen on 2009-04-08
I think you should check this:

[http://ubuntuforums.org/showthread.php?t=1113084&highlight=nomachine](http://ubuntuforums.org/showthread.php?t=1113084&highlight=nomachine)

I think you need to down grade gnome-panels

---

