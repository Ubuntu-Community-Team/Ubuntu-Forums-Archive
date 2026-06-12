---
title: "No Sound Output After Installing XFCE/Ubuntu-Desktop"
date: 2017-06-12
forum: Desktop Environments
---

### Post by souvik2701 on 2017-06-12
So I Deployed my VPS and then Installed ubuntu-desktop, xfce4 & xrdp on my Ubuntu 16.04 (x86_64) using the following cmds.
```
[COLOR=#676767][FONT=proxima-nova]sudo apt-get update[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo apt-get upgrade[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo apt-get install ubuntu-desktop[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo apt-get install xrdp[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo apt-get install xfce4[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]echo xfce4-session >~/.xsession[/FONT][/COLOR]
[COLOR=#676767][FONT=proxima-nova]sudo service xrdp restart[/FONT][/COLOR]
```

And then Accessed my Ubuntu Desktop via RDP. But, sadly while trying to run any sound files no sound is coming.
I'm a newbie with ubuntu GUI, I just used ubuntu for hosting websites a couple of times, I believe I'm missing something.

Any kind of help will be appreciated.
Have a great day.

---

