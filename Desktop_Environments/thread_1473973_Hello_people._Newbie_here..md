---
title: "Hello people. Newbie here."
date: 2010-05-05
forum: Desktop Environments
---

### Post by AjI2010 on 2010-05-05
Hello people.
 
My first post here on the forums.
 
Just to let you know that I am a TOTAL newbie with ubuntu and I am also not knowledgable with code or anything like that. 
You're all thinking "great!, not another one!"......but I am willing to learn.
 
 
I have chosen ubuntu because I am sick of windows and the constant crashing and various virus/malware attacks etc.
 
So as the ubuntu adverts say...."its free, so give it a try".
 
 
Well my ubuntu 9.10 install seems to have worked, but I can not get a good resolution on my acer X223w monitor.
And I can not seem to get ubuntu to recognise my wireless home network.
 
 
Any help would be much appreciated.
(In total layman terms would be nice ;) )
 
Cheers.

---

### Post by roubman on 2010-05-05
I have a similar problem though mine is a bit more complex, but here is a website that might help you out
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
 
hope it helps

---

### Post by _0R10N on 2010-05-05
Welcome!!! ):P

Well, when in case of a fresh install, it's always recommended to update the system. You should run
```

sudo aptitude update
sudo aptitude upgrade

```That will upgrade several packages and fix a lot of bugs. After that, reboot your system and hopefully those problems will be gone.

Kind regards!

---

### Post by Alan James on 2010-05-05
> Well my ubuntu 9.10 install seems to have worked, but I can not get a good resolution on my acer X223w monitor.

You may need to install video card drivers. What type of video card do you have?

---

### Post by grumpy.medic on 2010-05-05
> **AjI2010 said:**
> Hello people.
Well my ubuntu 9.10 install seems to have worked, but I can not get a good resolution on my acer X223w monitor.
And I can not seem to get ubuntu to recognise my wireless home network.


Hi there. Even though I am not too familiar with your particular model, you might want to try the following:

[LIST]
[*]Hardwire your laptop to your router/modem for internet access
[*]Run the upate System>Administration>Update Manager. Click check and after it finishes on Install Updates
[*]After that check if you can see any changes in your resolution/wireless connectivity.
[*]If not, got to System>Administration>Hardware Drivers after reconnecting your hardwire (Cat5)
[*]If it lists drivers to install, go ahead and install them, then restart and try resolution/wireless again. If it STILL does not work, chime back in and we can get more creative.
[/LIST]

I hope this helps a little. Like said, if it does not work out, drop us another line.

Cheers!

---

### Post by AjI2010 on 2010-05-06
> **_0R10N said:**
> Welcome!!! ):P
 
Well, when in case of a fresh install, it's always recommended to update the system. You should run
```

sudo aptitude update
sudo aptitude upgrade

```That will upgrade several packages and fix a lot of bugs. After that, reboot your system and hopefully those problems will be gone.
 
Kind regards!
 
Cheers.
 
When you mention 'CODE' ..... how do I enter this into ubuntu?
(yes....TOTAL newbie question I know!) :)
 
I will try this as a first step and then progress onto the other suggestions mentioned already.

---

### Post by sakundiak on 2010-05-06
Go to Applications/accessories/terminal and enter it there only if you have internet access. Also like grumpy.medic said you may want to connect directly to your router and see what's available for restricted drivers. There may be an nvidia driver or a wireless driver that will have to install before you can get it running good. Once hook up to the net go to System/Administration/Hardware drivers and see what's available. Good luck and welcome to the ubuntu side!

---

### Post by _0R10N on 2010-05-06
> **AjI2010 said:**
> Cheers.
 
When you mention 'CODE' ..... how do I enter this into ubuntu?
(yes....TOTAL newbie question I know!) :)
 
I will try this as a first step and then progress onto the other suggestions mentioned already.

Yeah, you must run those commands on your commandline. The title "Code" is added by the tool that manages the forums automatically.

Kind regards!

---

### Post by FirstByté on 2010-05-06
> **AjI2010 said:**
> Hello people.
 
*[...]*
 
I have chosen ubuntu because I am sick of windows and the constant crashing and various virus/malware attacks etc.
 
 
Any help would be much appreciated.
(In total layman terms would be nice ;) )
 
Cheers.

Welcome buddy, you are right on track, I came this way for same reason and loving my Ubunt&#378; daily :p

> **grumpy.medic said:**
> Hi there. Even though I am not too familiar with your particular model, you might want to try the following:

[LIST]
[*]Hardwire your laptop to your router/modem for internet access
[*]Run the upate System>Administration>Update Manager. Click check and after it finishes on Install Updates
[*]After that check if you can see any changes in your resolution/wireless connectivity.
[*]If not, got to System>Administration>Hardware Drivers after reconnecting your hardwire (Cat5)
[*]If it lists drivers to install, go ahead and install them, then restart and try resolution/wireless again. If it STILL does not work, chime back in and we can get more creative.
[/LIST]

I hope this helps a little. Like said, if it does not work out, drop us another line.

Cheers!

Following Grumpy.Medic should '&#324;ormally' work as a charm since Ubuntu 9.04. It *should* sense the proprietary [/restricted] hardware and prompt you for installation. As advised, plug a LAN cable wait for few minutes, all should be charm!
Canonical is covering strides with every release.

You are most welcome! :guitar:

---

### Post by grumpy.medic on 2010-05-06
> **AjI2010 said:**
> Cheers.
 
When you mention 'CODE' ..... how do I enter this into ubuntu?
(yes....TOTAL newbie question I know!) :)
 
I will try this as a first step and then progress onto the other suggestions mentioned already.

I apologize... sakundiak is correct, whenever code is mentioned you type it in what is known as the Terminal. You might as well make a link for it, as you will be (even as a new user) frequently performing tasks in it. It makes life... a little easier.

I am really curious if this works for you... please let us know.

Cheers!

---

