---
title: "ssh failed to appreciate the PATH environment variable"
date: 2012-11-22
forum: Desktop Environments
---

### Post by evandenrijd on 2012-11-22
Hi,

I upgraded recently to Ubuntu 12.04 LTS.
I installed the default sshd.
When I log into localhost the PATH environment variable seems to be not correctly set:

  van@dingo:~$ ssh -vvv localhost
  OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
  debug1: Reading configuration data /etc/ssh/ssh_config
  ...
  Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-33-generic-pae i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  Last login: Thu Nov 22 16:58:56 2012 from localhost
  debug3: Copy environment: PATH=/home/van/bin:$PATH
  debug3: Copy environment: LANG=en_US.UTF-8
  debug3: Copy environment:     XDG_SESSION_COOKIE=d00df1493f6acaebadf6bd000000000c-1353600439.973078-241131663
Environment:
  LANG=en_US.UTF-8
  USER=van
  LOGNAME=van
  HOME=/home/van
  PATH=/home/van/bin:$PATH
  MAIL=/var/mail/van
  SHELL=/bin/bash
  SSH_CLIENT=::1 34094 1234
  SSH_CONNECTION=::1 34094 ::1 1234
  SSH_TTY=/dev/pts/13
  TERM=xterm
  XDG_SESSION_COOKIE=d00df1493f6acaebadf6bd000000000c-1353600439.973078-241131663
  -bash: groups: command not found
  Command 'uname' is available in '/bin/uname'
  The command could not be located because '/bin' is not included   in the PATH environment variable.
  uname: command not found
-bash: [: =: unary operator expected
  Command 'sed' is available in '/bin/sed'
  The command could not be located because '/bin' is not included   in the PATH environment variable.
  sed: command not found
  Command 'ls' is available in '/bin/ls'
  The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found
  van@dingo:~$ echo $PATH
  /home/van/bin:$PATH
  van@dingo:~$ /bin/cat /etc/environment 
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

As you can see that /etc/environment contains the correct PATH, it is not correctly set.

Any ideas?

---

### Post by markbl on 2012-11-22
Sure you are not overriding PATH anywhere in your ~/.bashrc, ~/.bash_profile, or ~/.profile?

---

### Post by papibe on 2012-11-22
Hi evandenrijd. Welcome to the forums ):P

I believe that while trying to add your ~/bin the the PATH, you wrongly overwrote it.

For instance, this is my PATH with my ~/bin on it:
```
echo $PATH
/home/user/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

Yours looks incorrectly set:
> **evandenrijd said:**
> van@dingo:~$ echo $PATH
  /home/van/bin:$PATH


BTW, you don't have to do anything to include your ~/bin into the PATH. By default Ubuntu looks for it. If it finds it, it adds it to the PATH.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by evandenrijd on 2012-11-23
Hi, I checked that but I didn't change my PATH variable in .bashrc

I only have:
van@dingo:~$ ls -lrt ~/.bash*
-rw-r--r-- 1 van van  220 May  7  2012 /home/van/.bash_logout
-rw-r--r-- 1 van van 3487 May 22  2012 /home/van/.bashrc
-rw------- 1 van van 9244 Nov 23 09:59 /home/van/.bash_history
van@dingo:~$ ls -lrt ~/.profile
ls: cannot access /home/van/.profile: No such file or directory

So indeed I really wonder what script changed the PATH variable.
Remark that it only happens in ssh context, if I start a new bash terminal my PATH resembles yours.

Any other ideas?

---

### Post by papibe on 2012-11-23
Could you post the content of your ~/.bashrc ?

---

### Post by evandenrijd on 2012-11-26
Hi, sure, you'll find it in attachement.

---

### Post by efflandt on 2012-11-28
One question is what happened to your /home/van/.profile, and the other is, how are you adding /home/van/bin to your $PATH?

default ~/.profile normally contains:

```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```Also when I **ssh -vvv localhost** (which shows same version OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012) I do not see any "Copy environment", although, I do see: **debug1: Sending environment.** and a list of debug 3: env variables that it ignores, other than **debug1: Sending env LANG = en_US.UTF-8**.  There is no mention at all of PATH other than **debug3: Ignored env MANDATORY_PATH** (which I would think would be set by the shell you log into).  So not sure where your **debug3: Copy environment:** lines are coming from.

```
efflandt@XPS8100-1204:~$ env
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=994d44c0ee8f1422ac85e8ee00000007-1354161407.118821-1525725162
SSH_CLIENT=127.0.0.1 37152 22
SSH_TTY=/dev/pts/2
USER=efflandt
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36:
MAIL=/var/mail/efflandt
PATH=/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/efflandt
LANG=en_US.UTF-8
SHLVL=1
HOME=/home/efflandt
LOGNAME=efflandt
SSH_CONNECTION=127.0.0.1 37152 127.0.0.1 22
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=localhost:10.0
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env
```

---

### Post by evandenrijd on 2012-11-30
Hi, good point, where does the /home/van/bin come from if I do not have a .profile.

But I remember that in the past I had one, and with multiple hibernates and I probably still had a PATH within the desktop environment.

So, I restarted the machine, and indeed now my PATH is:
van@dingo:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin
:/usr/bin:/sbin:/bin:/usr/games

But still my orignal problem is still there, something changed my PATH in the ssh session, but I do NOT know what?!
ssh localhost
... (skipped error messages for details, see above)
van@dingo:~$ echo $PATH
/home/van/bin:$PATH
van@dingo:~$ echo $SHELL
/bin/bash
van@dingo:~$ echo ${BASH_VERSION}
4.2.24(1)-release


PS. My original PATH comes from
van@dingo:~$ cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

---

### Post by evandenrijd on 2012-12-17
Found the solution, I had a pam environment file, which I happily removed.

Thanks for all effort.

van@dingo:~$ cat .pam_environment
PATH=/home/van/bin:$PATH

---

