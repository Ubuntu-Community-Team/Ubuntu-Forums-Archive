---
title: "Installing Graphics Drivers Help"
date: 2008-12-22
forum: General Help
---

### Post by geudrik on 2008-12-22
First and foremost I am a complete beginner when it comes to Linux in general, but Ubuntu specifically.

I decided that I was sick of vista to the point of migration yesterday but I do need a little help getting going.

The first thing I need to do (after installing updates, which I'm doing now) is get my graphics drivers in.  I have an nVidia Quadro FX 1700 in my Compaq 8710w Laptop.  I downloaded the graphics driver package (.run) to my desktop.  Then I bound the windows logo key to open a terminal window.

In order from the time I open a terminal window, these are the commands I enter...

cd Desktop  -> puts me onto my desktop as the working dir.
sudo sh NVIDIA-Linux-x86-177.82-pkg1.run
[sudo] password for XXX: *******

Lots of .................

"You appear to be running an X server. Please close the X server before continuing."

When I entered 
sudo /etc/init.d/gdm stop
ubuntu died... I got a black screen and then a blinking cursor that did nothing.

From what I've read, root no longer really exists as a user.  sudo is the command that you enter if you need to run something as root (I do a lot of Ruby programming - that's the only reason I know some commands)

So, how do I get my graphics drivers installed correctly?

Thanks
Pat

---

### Post by taurus on 2008-12-22
First, look in System -> Administration -> Hardware Drivers to see if your graphic card is in the list.  It's easier to install driver from there.

Otherwise, press <Ctrl><Alt>F2 and log in with your username and password.  Then, kill gdm and install the download driver with

```
sudo /etc/init.d/gdm stop
cd ~/Desktop
sudo sh NVIDIA-Linux-x86-177.82-pkg1.run
```

Once it's done, see if X works again.

```
sudo /etc/init.d/gdm start
```

Make sure the driver that you downloaded is for your graphic card because it could crash your X server.

---

### Post by eldragon on 2008-12-22
im no nvidia wizz.......but i think, you can have your display graphics installed using the restricted driver setup from system / administration. im not sure though.

to have x running again, do the following:

hit ctrl-alt-f1

login with your adm user.

run 
```

$ sudo /etc/init.d/gdm restart

```

you should be back at the login screen.

---

### Post by Twitch6000 on 2008-12-22
If you are using the stable driver (177) there is no need to download and use the terminal.

Just go to System -> Administration -> Hardware Drivers.

Click the recommended driver and install. It will take a bit,but after that hey restart and boom its ready =].

Now if you want to use the beta driver(very good driver) you would need to use the .run file.

---

### Post by geudrik on 2008-12-22
Thanks guys.  I think I got the graphics drivers installed correctly.  How do I figure out if they really did go in right?  I mean, in windows all I had to do was go into the device manager and see what showed up for Display adapters.  

And why the differences between the two replys?

When I stopped the x server, it went back to being no gui and I entered taurus' commands and the driver said it was installing.  Then i just restartedt he server... using Start, not restart and everything seems to be working ok.

Am I to assume however that Ubuntu or linux in general hasn't made it far enough to really be able to game?  The only reason I ask this is:

When i scroll through web pages there is no more tearing, but when im streamin audio in the media player the visualizer is still somewhat laggy, and its only a 500x400 window (roughly)

-Pat

---

### Post by Twitch6000 on 2008-12-22
> **geudrik said:**
> Thanks guys.  I think I got the graphics drivers installed correctly.  How do I figure out if they really did go in right?  I mean, in windows all I had to do was go into the device manager and see what showed up for Display adapters.  

And why the differences between the two replys?

When I stopped the x server, it went back to being no gui and I entered taurus' commands and the driver said it was installing.  Then i just restartedt he server... using Start, not restart and everything seems to be working ok.

Am I to assume however that Ubuntu or linux in general hasn't made it far enough to really be able to game?  The only reason I ask this is:

When i scroll through web pages there is no more tearing, but when im streamin audio in the media player the visualizer is still somewhat laggy, and its only a 500x400 window (roughly)

-Pat
This is just the getting use to no windows stage.

For your audio problem this fix is just like the fix in windows.

You need the codecs.

Go to add/remove and get the restriced extras. I also suggest going into the package manager and typing libdvdcss2 and downloading that.

After doing so your audio should be just fine. If any more audio problems then happen just say so.

---

