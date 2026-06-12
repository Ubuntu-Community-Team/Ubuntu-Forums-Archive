---
title: "startup sudo"
date: 2009-04-11
forum: General Help
---

### Post by Baconfatty on 2009-04-11
Ok I'm trying to run sudo shutdown -r 30 at start up however it needs a password to start it is there a way to get around this?

---

### Post by calvinps on 2009-04-11
> **Baconfatty said:**
> Ok I'm trying to run sudo shutdown -r 30 at start up however it needs a password to start it is there a way to get around this?

**sudo** is a thing that if you run something in a terminal, you will require a password for it. So there's no way around it.

---

### Post by kerry_s on 2009-04-11
you have to use the "NOPASSWD:" switch in visudo.

example:

you ALL=(ALL) NOPASSWD: /path/to/your/script


"man sudo" for more details.

---

### Post by Baconfatty on 2009-04-11
so your saying enter guest NOPASSWD: sudo shutdown -r 30 will make it work?

---

### Post by kerry_s on 2009-04-11
> **Baconfatty said:**
> so your saying enter guest NOPASSWD: sudo shutdown -r 30 will make it work?

is "guest" you?

```
guest ALL=(ALL) NOPASSWD: /sbin/shutdown, /sbin/reboot, /sbin/halt, /sbin/poweroff 
```

that should cover all the shutdown options.

---

### Post by Dejavou42 on 2009-04-11
I have an entry in my sudoers file that should allow me to run a script with out a password.

```
windowsxp ALL=(ALL) NOPASSWD: /home/scripts/myscript
```

I also have this same script starting up when the user logs in. 

The script runs a command through gksu.

However, when I log into the user, the script loads but still prompts for a password.

Any thoughts?

---

### Post by kerry_s on 2009-04-12
sudo is for the script, if you have sudo in the script it don't count.
example:
your startup should be like> gksudo your-script
not
your-script <with gksudo in it.

take the gksu out of the script and run the whole script as "gksudo your-script".

sorry, tired eyes, anyways you don't need the "gk" just "sudo" is fine cause your running no password.

---

### Post by Dejavou42 on 2009-04-12
I just tried to remove sudo from the script and use sudo to run the script. However, I was still prompted for a password.

Just for reference, here is the script and the commands that I have used to run it. 

```

VBoxSDL -fullscreen -vm myvm

### Previously, the command was:
gksu VBoxSDL -fullscreen -vm myvm

```

I tried to run the script both ways with the absolute path to the script from terminal with and without sudo and gksu. Every time I am prompted for a password.

Here is the entry in /etc/sudoers that should allow this operation without a pass:

```


myuser ALL=(ALL) NOPASSWD: /home/scripts/Vboxscript

## I have also tried this configuration by granting group access with:

%mygroup ALL=(ALL) NOPASSWD: /home/scripts/Vboxscript

```

Thanks for the help!

---

### Post by kerry_s on 2009-04-12
why would you want to run vbox as root? that is a huge security issue.

---

### Post by miegiel on 2009-04-12
> **kerry_s said:**
> why would you want to run vbox as root? that is a huge security issue.

Yeah, I was thinking some of these suggestions don't seem safe to me. :twisted:

---

### Post by kerry_s on 2009-04-13
> **miegiel said:**
> Yeah, I was thinking some of these suggestions don't seem safe to me. :twisted:

learning to use it is fine, doing something that shouldn't be done, well i just chalk it up to learning. just tell them it's not right and let them do there thing. ;)

---

### Post by Baconfatty on 2009-04-13
> **kerry_s said:**
> is "guest" you?

Its running on a public use pc so guest is for the customers.

---

### Post by Baconfatty on 2009-04-13
oh and if I go 

```
guest ALL=(ALL) NOPASSWD: /sbin/reboot 30
```

will that give me 30sec or 30 min?

---

### Post by Baconfatty on 2009-04-13
```
guest ALL=(ALL) NOPASSWD: /sbin/reboot
bash: syntax error near unexpected token "('
```


what??

---

### Post by kerry_s on 2009-04-13
> **Baconfatty said:**
> oh and if I go 

```
guest ALL=(ALL) NOPASSWD: /sbin/reboot 30
```

will that give me 30sec or 30 min?

no, you can't do that.
just put:
**guest ALL=(ALL) NOPASSWD: /sbin/reboot**

then use a script for the time:

[B]#!/bin/sh
sleep 1800
sudo reboot[/B]

---

### Post by Baconfatty on 2009-04-14
script?

---

### Post by Dejavou42 on 2009-04-14
> **kerry_s said:**
> why would you want to run vbox as root? that is a huge security issue.

I know that it's a security issue, and I am fully aware of the risk. I have been running Vbox as root to give multiple users access to the VM. I also have my VM on a different hard drive, and it has no access to my linux box.

Can I not run the script without a password because of the location of the script? Should I copy the script to sbin to get it to work?

> **Baconfatty said:**
> how do I write the script and what not?  sorry I'm new to this could someone walk me through it.

Right click on desktop > Create Document > Empty File

Paste the #! /bin/bash script that kerry_s gave you, save, and close.

Next, Right click the new file, click properties,click the permissions tab, and place a check mark by execute.

---

### Post by Baconfatty on 2009-04-15
ok so in seasons at start up i put 

guest ALL=(ALL) NOPASSWD: /sbin/reboot2

then in /sbin i created a file called /reboot2 with the following

#!/bin/sh
sleep 1800
sudo reboot

and its still not doing anything

oh and /reboot2 is executable

something im missing?

---

### Post by kerry_s on 2009-04-15
> **Baconfatty said:**
> ok so in seasons at start up i put 

guest ALL=(ALL) NOPASSWD: /sbin/reboot2

then in /sbin i created a file called /reboot2 with the following

#!/bin/sh
sleep 1800
sudo reboot

and its still not doing anything

oh and /reboot2 is executable

something im missing?

no, this go's in visudo:
**guest ALL=(ALL) NOPASSWD: /sbin/reboot**

this would go in session, but /sbin is not the place it should be:
**/sbin/reboot2**

this is your script, you should put personal scripts in /usr/local/bin
[B]#!/bin/sh
sleep 1800
sudo reboot
[/B]
for session:
**/usr/local/bin/reboot2**

i also think you should give a warning before the reboot.
in session:
**sleep 1740;xmessage " You have 1 minute to finish! " -center**

you might have to script that:
[B]#!/bin/sh
sleep 1740
xmessage " You have 1 minute to finish! " -center[/B]

it would look something like this, see pic>
you can also use zenity, if that's installed, see pic>
zenity --warning --text "You have 1 minute to finish"

---

### Post by Baconfatty on 2009-04-15
sorry to sound like a noob but how do I add 
guest ALL=(ALL) NOPASSWD: /sbin/reboot 
to visudo

then after that,
this goes in bin

#!/bin/sh
sleep 1800
sudo reboot

and this goes in session

/usr/local/bin/reboot2

and /sbin/reboot2 gets discarded right?

---

### Post by kerry_s on 2009-04-15
> how do I add
guest ALL=(ALL) NOPASSWD: /sbin/reboot
to visudo

in a terminal type> **sudo visudo** <see pic

> this goes in bin

#!/bin/sh
sleep 1800
sudo reboot

**/usr/local/bin**

in terminal type> **gksudo /usr/local/bin/reboot2**
put:
[B]#!/bin/sh
sleep 1800
sudo reboot[/B]

> and this goes in session

/usr/local/bin/reboot2

yes

> and /sbin/reboot2 gets discarded right? 

yes

---

### Post by Baconfatty on 2009-04-17
ok this is what I have and its still not working

[IMG]http://i18.photobucket.com/albums/b133/BaconFatty/Screenshot.png[/IMG]
[IMG]http://i18.photobucket.com/albums/b133/BaconFatty/Screenshot-1.png[/IMG]
[IMG]http://i18.photobucket.com/albums/b133/BaconFatty/Screenshot-2.png[/IMG]

---

### Post by Baconfatty on 2009-04-18
bump

---

### Post by Baconfatty on 2009-04-22
any one?

---

### Post by kerry_s on 2009-04-22
is guest in the "sudo" group to be able to use sudo?

in terminal:
**cat /etc/group | grep sudo**
or
**cat /etc/group | grep guest**
to see what group guest is in.

---

### Post by Baconfatty on 2009-04-24
This is what came up

```
guest@Public:~$ cat /etc/group | grep sudo
sudo:x:27:

guest@Public:~$ cat /etc/group | grep guest
dialout:x:20:cupsys,bob,guest
dip:x:30:bob,guest
admin:x:117:bob,guest
fuse:x:119:guest
guest:x:1001:
guest@Public:~$ 
```

---

### Post by Baconfatty on 2009-04-27
this mean anything?

---

### Post by vistadude on 2009-04-27
Idk If this will work, but u might want to try gksudo instead of sudo, I beleave gksu would work to

---

### Post by Baconfatty on 2009-04-28
Isn't gksudo just the gui for terminal?

---

### Post by vistadude on 2009-04-28
well i can't really say im all to sure about that, but it is a command and sudo is also a command and u r trying a command here, so if sudo would work gksudo should also

---

### Post by kerry_s on 2009-04-28
```
guest@Public:~$ cat /etc/group | grep sudo
sudo:x:27:
```


your guest is not in the sudo group, it's blank.

do> sudo visudo

and add guest to "sudo" and "power" group.

---

### Post by Baconfatty on 2009-04-28
> **vistadude said:**
> well i can't really say im all to sure about that, but it is a command and sudo is also a command and u r trying a command here, so if sudo would work gksudo should also

the problem isnt getting sudo to work in terminal, its getting it to work in session on start up with out having to put in the password for it.

And I will give that a try karry.

---

### Post by Baconfatty on 2009-05-21
Ok I did what you said adding the guest to power group, well I think I did is this right

[http://i18.photobucket.com/albums/b133/BaconFatty/Screenshot3.png](http://i18.photobucket.com/albums/b133/BaconFatty/Screenshot3.png)

---

### Post by Baconfatty on 2009-05-22
bump

---

### Post by Baconfatty on 2009-05-24
bump

---

### Post by Baconfatty on 2009-06-04
anyone know?

---

