---
title: "NetZero Dialup for Breezy Badger"
date: 2006-03-25
forum: Desktop Environments
---

### Post by sliverman69 on 2006-03-25
I have had linux for about a week now and have learned a great deal about how it works.  I am a student learning to become a programmer/engineer.  Anyway I have learned how to change a winmodem into a linmodem and all that is left for me to do now is get netzero to work.  I have done the command "sudo dpkg -i netzero.deb" then it said something to the degree that it was unpacking it and installing it.  But when I looked in the filesystem I could not find a trace of anything but the netzero.deb file.  Anyway, I was wondering if anyone could help give me a step-by-step guide to installing netzero.
Thanks so very much,
Bret

---

### Post by sliverman69 on 2006-03-26
As i accumulate more data on installing net zero on breezy badger I will update instructions on how to do so.  Every command I give will be using the terminal window which can be found on the application menu in system (I think that is the first folder in that menu).

1. Download the Netzero.deb file from [http://my.netzero.net/s/download]("http://my.netzero.net/s/download") (this won't work if you are not a member of netzero)

2. Download java (I haven't figured out if it is the runtime environment or what)

3. Load these files on a flash drive or some other storage device(s)

4. boot up ubuntu

5. copy the files to the home directory in ubuntu

6. install java with their linux instructions (probably something like: "sudo dpkg -i <filename>.deb or whatever the file extension is)

7. install netzero by the following command: sudo dpkg -i netzero.deb
(this should extract and install the files to /opt/nzclient)

that is all I have so far.  I hope to find more and then I will be happy to post it.

---

### Post by towsonu2003 on 2006-03-26
check out [http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=7020&forum=18](http://www.pclinuxonline.com/modules.php?mop=modload&name=Splatt_Forums&file=viewtopic&topic=7020&forum=18)

if you can get it up and running, you could add the howto to the wiki (second link in my signature) as a new Heading1 at the bottom I guess.

---

### Post by sliverman69 on 2006-03-27
towsonu2003,

I tried the instructions on the page that you had.  either I didn't have java installed.  (I installed two different java programs j2re 1.40 and jre 1.50) I don't know if i removed the 2nd java package or not, but I do know that I keep getting a message that says: DM set to off

does anyone know what is wrong.

If it is java could you supply a link to where I could get it.

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=sliverman69]
I tried the instructions on the page that you had.  either I didn't have java installed.  (I installed two different java programs j2re 1.40 and jre 1.50) I don't know if i removed the 2nd java package or not, but I do know that I keep getting a message that says: DM set to off
[/QUOTE]
huh? I have no idea what DM is... While waiting for a response here, I would post to that thread as well. You never know who's watching. 

Did you try dialing with wvdial (second link in my signature, bottom of the page)? If you know the phone #, username, and passwd -> it may work...

---

### Post by sliverman69 on 2006-03-27
I have not tried the wvdialer, but I do know that netzero will not let you log onto their server unless you are using their software.  I have tried this before in windows and failed and I looked at a number of resources that say the same thing.  However, in linux I have not been able to with the ppp dialer.  Also, I do not know how to use wv dialer or if I even have it.

---

### Post by towsonu2003 on 2006-03-27
[QUOTE=sliverman69]I have not tried the wvdialer, but I do know that netzero will not let you log onto their server unless you are using their software.  I have tried this before in windows and failed and I looked at a number of resources that say the same thing.  However, in linux I have not been able to with the ppp dialer.  Also, I do not know how to use wv dialer or if I even have it.[/QUOTE]
what's the output of ```
java -version
```
do netzero help you with installation of this package? maybe they'd know what "DM is set to off" means?
and finally, did you post to that forum? there's always a chance someone knows the answer. Make sure you specify the error it gives. 

Let's give wvdialer a chance in the meantime. Do the following:
```

#insert Ubuntu installation CD to drive and make sure it **is** mounted
sudo apt-get update
sudo apt-get install wvdial
sudo wvdialconf /etc/wvdial.conf #this will configure wvdial, which should detect the modem automatically
sudo gedit /etc/wvdial.conf
```
Put your username, password, and phone number in that file, where marked. there should be no ; or # (or anything else) at the beginning of those lines. Append the following two lines at the end of the file as well:
```

Carrier Check = no
Stupid Mode = yes

```
save and close. and connect with ```
sudo wvdial
```if it doesn't connect, remove the above 2 lines, try again. doesn't connect again? put 1 line back in. not connecting? remove 1st line put 2nd line back. You get the idea: combining options...

It may not connect at first try. try and re-try for 15 minutes. I usually connect after 4-7 tries.

---

### Post by djheadley on 2006-03-27
I added this line to the beginning to my runclient.sh file:

ln -s /dev/ttyS3 /dev/modem

As for the message, try running runclient.sh a second time, I usually have to run it twice to get it to connect.

---

### Post by sliverman69 on 2006-03-29
I borrowed my friend's Kubuntu cd so that I could install the KDE desktop.  So, I am starting over from scratch.  Hopefully, I can get it to work this time around.  I will be installing the modem driver first since I have a soft modem from Intel.  I have the Intel 537 EP PCI softmodem. I had it working with the gnome desktop so I think that the same .bin file will work just the same.  Anyway I won't be available any more today because I will be working on that, plus I am going to see *Phantom of the Opera* tonight (not the movie version).

---

### Post by sliverman69 on 2006-03-29
If all of the previous instructions fail, then I will use these wonderful suggestions you have put forth in posts #7 and #8

---

### Post by sliverman69 on 2006-03-30
I recently installed Kubuntu, so I have to start over from scratch.  Maybe this will help me to get it right and not mess it up.  The only problem is when I installed Kubuntu, I think I need some other files because when I log in it won't let me have Admin. rights or log in as the root user.  I wish I knew what I could do to fix it.  Anyway, I am  going to reinstall Kubuntu in hopes of fixing the problems I am having logging in as root using sudo commands and using admin rights.  If anyone knows how to fix this without reinstalling, the help would be much appreciated.

Thanks.

---

### Post by sliverman69 on 2006-04-16
i have dsl now, so I don't need instructions on installing net zero anymore.  However, I will try to get net zero installed using some instructions someone e-mailed me and then I will post back if they work.  I want all of you to be able to access the internet on linux, so I am going to do all I can to help.

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=sliverman69]i have dsl now, so I don't need instructions on installing net zero anymore.  However, I will try to get net zero installed using some instructions someone e-mailed me and then I will post back if they work.  I want all of you to be able to access the internet on linux, so I am going to do all I can to help.[/QUOTE]
great, thanks :)

---

### Post by sliverman69 on 2006-04-16
once I finish downloeading ragnarok online I am going to try to get the net-zero working...I had managed to get my winmodem working so all that was left to do was get netzero working...I am going to get that working so that if our dsl is ever not working I can use netzero to get online.

---

### Post by sliverman69 on 2006-04-16
I also plan on switching to suse 10 linux, because I have heard that it is more stable and awesome

---

### Post by sliverman69 on 2006-04-16
nothing against ubuntu, but I have heard that there are less bugs in the distro.

---

### Post by towsonu2003 on 2006-04-16
I'm smelling a flamewar :PpPpPp

it's (suse) gonna release 10.1 soon -you might wanna wait for that-

---

### Post by sliverman69 on 2006-04-16
they already have the security updates and stuff out for it.

---

