---
title: "Running &quot;x2goclient&quot; on Android devices ... sort of"
date: 2021-07-21
forum: Desktop Environments
---

### Post by scorp123 on 2021-07-21
I'm posting this here in the hope that others who are looking for a way to have any kind of **X2go Client** on their **Android device** might find it, e.g. via Google. It sure would have helped me had I found a forum post like this...  So to spare you from wasting many hours trying to figure this out like I just did, I will write this down. Hopefully it will be useful to someone some day.

So, as we all know, there is **_no native Android client for the "X2go"_** remote desktop solution. Which is a big shame. "X2go" is a lot faster than e.g. VNC, it is also more secure, it can work with SSH keys, SSH jump hosts, it can forward sound, it can reconnect to an already running desktop session...  there are so many ways it is superior to VNC.

Having a X2go client on your Android device sure would be *"nice to have"*. In my case it's even *"must have"* because sometimes I really really need full desktop access to my Linux machines back in the office and a simple SSH session won't be sufficient in all scenarios. And it could happen that I don't have my laptop with me... just my Android 'phablet' (yes, I'm a huge fan of plus-size Android devices!). 

Since there simply is **_no X2go Android client_** we are going to cheat by installing a so called *"Linux compatibility layer"* on our Android device.

I have experimented with these 3:

[LIST]
[*][Andronix]("https://play.google.com/store/apps/details?id=studio.com.techriz.andronix")
[*][Debian Nonroot]("https://play.google.com/store/apps/details?id=com.cuntubuntu")
[*][UserLand]("https://play.google.com/store/apps/details?id=tech.ula")
[/LIST]

I have had issues and various problems with all 3 x ... but **UserLand **seems to work best (as of July 2021). So that's what I'm going with here.


**_Step 1:_**

Install **"UserLand"** from the Google Play Store: [https://play.google.com/store/apps/details?id=tech.ula]("https://play.google.com/store/apps/details?id=tech.ula") ...
You will also need a VNC client to connect to your fake Linux desktop that will be running locally on your Android device.

For most people this one should do:
[https://play.google.com/store/apps/details?id=com.realvnc.viewer.android]("https://play.google.com/store/apps/details?id=com.realvnc.viewer.android")

I myself bought this one because it also works very nicely with the "DeX" (desktop mode) of my Samsung device:
[https://play.google.com/store/apps/details?id=com.iiordanov.bVNC]("https://play.google.com/store/apps/details?id=com.iiordanov.bVNC")


**_Step 2:_**

Once "UserLand" is installed you should be seeing a screen that offers you various icons, e.g. Alpine Linux, Debian and Ubuntu sessions ... Scroll down until you find the "LXDE" and "XFCE" desktop sessions. Now create a local desktop session for VNC, e.g. by telling "UserLand" to install Ubuntu with either the XFCE or the LXDE desktop for you. "UserLand" will ask you to define a user account and a VNC password:

[ATTACH=CONFIG]288844[/ATTACH]
(UserLand in Samsung's DeX mode)

Once you have a user and a VNC password, "UserLand" will offer you to connect to your new environment:

[ATTACH=CONFIG]288845[/ATTACH]

When you connect you should find yourself in a minimalist **"twm"** session and there should be a terminal which is busy with installing lots and lots of packages for you...

[ATTACH=CONFIG]288846[/ATTACH]

When everything is done, you will be told to disconnect from this VNC session, stop it (you will find it on the "Sessions" tab of "UserLand" ... long-press it and then choose "Stop"), restart it, and then reconnect to it (by clicking on it on the "Sessions" tab). When you do then this time you should be greeted by your chosen desktop, e.g. XFCE:

[ATTACH=CONFIG]288847[/ATTACH]

Now, this desktop behaves exactly like a 'normal' Linux VM would, e.g. you can install additional themes, additional wallpapers, icons, customize it whichever way you want. Don't forget to run updates:
```
sudo apt update
sudo apt dist-upgrade
```


**_Step 3a:_**

Now you can install "x2goclient" like you would inside a Linux VM or a normal Ubuntu desktop:
```
sudo apt install x2goclient
```


**_Step 3b:_**

Now, if you try to run your X2go client you will run into various errors, such as:
```
error while loading shared libraries: libdl.so: cannot open shared object file: No such file or directory
```

... or:
```
error while loading shared libraries: /usr/lib/aarch64-linux-gnu/libc.so: invalid ELF header
```


The core reason for this is a bug in "UserLand". Some nice folks already filed a bug report:
[https://github.com/CypherpunkArmory/UserLAnd/issues/1410]("https://github.com/CypherpunkArmory/UserLAnd/issues/1410")

So to work around this bug you have to set a specific environment variable to an empty value:
```
export LD_LIBRARY_PATH=""
```

I'd also recommend to add that line into various places such as your **~/.bashrc**, **~/.profile** ...

It appears that the developers were aware of the problem and they tried getting rid of the problem by defining commands such as
```
unset LD_LIBRARY_PATH
```

... in various places such as **/etc/profile.d/userland.sh**  ... except this does not seem to have any positive effect.

Anyways.... until this bug is solved executing the command...
```
export LD_LIBRARY_PATH=""
```

... will work tip top and achieve the desired effect.

Once this variable is cleared you should be able to execute the X2go client:
```
x2goclient
```

X2go client running on the "openbox" window manager, running inside an Ubuntu VM, running on Android 11, showing a remotely running Ubuntu-Budgie session:

[ATTACH=CONFIG]288848[/ATTACH]


Until such time that we get blessed with an official Android client for X2go or a working HTML5 implementation (so we could access X2go with our web browsers) I guess this is a suitable workaround for Linux road warriors who need X2go access on the go via their Android devices ...

---

### Post by ActionParsnip on 2021-07-21
Nef you do this you should see if there is a sleeker solution. Like SSH or Web interfaces which apps can connect to (VLC and Transmission spring to mind). A lot of the time there is a better option than accessing the full desktop. People (a lot of the time) just jump to VNC and similar without thinking. I've had users VNC to a remote system on their own LAN, to then open a Web browser to [http://localhost](http://localhost)
I kid you not

---

### Post by scorp123 on 2021-07-21
> **ActionParsnip said:**
> Nef you do this you should see if there is a sleeker solution.

Sure, for many things a simple SSH terminal or a SSH tunnel (e.g. for forwarding a remote web site to your local device) will suffice. There are many excellent SSH clients on Android, both free and paid ones. And SSH tunnelling isn't too hard. But I have a few use cases where SSH won't be enough and where I absolutely need a full desktop *somehow*. And what if my employer's Citrix infrastructure isn't working in that moment because the Windows guys had to take it down once again because of some urgent security issue...? :-k  That has happened a few times lately thanks to all the Citrix zero-day exploits that are going around. ](*,)  Sure, I could wait until the Windows folks get their Citrix stuff up and running again... but then again I hate to be depending on them and the "reliability" (read: complete lack thereof) of their stuff #-o  so I'd very much prefer to have my own solution that does not have Windows anywhere in the equation. So I can do the job I'm paid to do. 8-)

And running X2go this way works surprisingly well. \\:D/  And having something like a "Linux VM" (UserLand's compatibility layer) locally on my Android device that's actually working and behaving like the real thing? Can't say I dislike the idea... :D

---

### Post by ActionParsnip on 2021-07-21
I manage Windows entirely with Powershell. I don't suggest you use VNC to Windows servers and IMHO RDP should not be used by engineers to resolve issues on servers.
The only real use case for this I can see, is remote desk side support etc. For real servers it's pretty awful but then again people install webmin etc which is also pretty nasty

---

