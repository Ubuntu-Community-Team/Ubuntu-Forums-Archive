---
title: "how to install compiz fusion?"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by damansandhu on 2007-08-15
ok , i am new in ubuntu 7.04 , i installed beryl yesterday and its not working , when i run beryl manager nothing hapens , i have geforce 7600gs and drivers are properly installed , moreover i cannot select themes from emrald theme manager because there is no apply option in it , if you know how to install compiz fusion then plz explain it to me , and also tell how to apply themes , i am seriously bored with th default theme of ubuntu .

---

### Post by alphane on 2007-08-15
*cough* use the search function *cough*

Sounds like you're after a tutorial/how-to, of which there are loads on these forums already.

---

### Post by petit.padavoine on 2007-08-15
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29)

or compile it from source ;)

---

### Post by damansandhu on 2007-08-15
ok i am getting this error

daman@Ultimate:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Password:--16:44:44--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180         10.44K/s

16:44:46 (10.43 KB/s) - `-' saved [4180/4180]


daman@Ultimate:~$ gksudo apt-get update
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
daman@Ultimate:~$ gksudo apt-get -y upgrade
gksudo: invalid option -- y
GKsu version 2.0.0

Usage: gksudo [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --su-mode, -w
    Make GKSu use su, instead of using libgksu's
    default.
daman@Ultimate:~$ cp -p /etc/X11/xorg.conf /etc/X11/xorgold.conf
cp: cannot create regular file `/etc/X11/xorgold.conf': Permission denied
daman@Ultimate:~$ gksudo gedit /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
gedit: command not found
daman@Ultimate:~$

---

### Post by petit.padavoine on 2007-08-15
Use sudo, not gksudo.
But how come you don't even have gedit?
Are you running the server edition or something?

---

### Post by damansandhu on 2007-08-15
i am running ubuntu 7.04 fiesty desktop

---

