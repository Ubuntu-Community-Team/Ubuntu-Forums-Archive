---
title: "Remote Desktop Connection - black screen?"
date: 2009-02-03
forum: General Help
---

### Post by mykrob on 2009-02-03
I tested my remote desktop from within my LAN today, and it worked fine. I have it set to allow incoming connections and also selected the option to not have to not ask for confirmation. I set a password and forwarded port 5900 on my router to the static IP of the machine I want to control.

Now I am away, and when I attempt the remote connection, I simply get a black screen and no prompt for the password. 

Any idea what is happening? 

I want to set it to where I can always remote into my home machine if I need to .

Thanks,
-myk

PS running Ubuntu 8.10 with all updates installed

---

### Post by redilyn on 2009-02-03
Are you using vnc to do this?

---

### Post by mykrob on 2009-02-03
Using Vinagre
Applications-->Internet-->Remote Desktop Connection

I tried running it from console:

vinagre ##.#.##.##:5900

and it yielded no output, just put up the same black screen.

I know my screensaver is probably running at home, does this have anything to do with it? I figured the remote connection attempt would turn of the screensaver and just ask for the password..

---

### Post by redilyn on 2009-02-03
Can you try using the terminal server client and see if you have the same problem?

Applications -> Internet -> Terminal Server Client

Be sure protocol is set to vnc

If vnc is grayed out, try the following

```

sudo apt-get install vncviewer

```

Hopefully this will help.

You are correct, the screensaver should automatically turn off when you connect.

---

### Post by mykrob on 2009-02-03
using TSC, when I press connect, the app just disappears.

Running tsclient from the console, it seems the app is actually still running, I just get no output from the console either...

TSClient does work for connection to a Windows SBS2003 server I admin, so the tsclient app is not issue, i dont think. Is there something in my configuration of my desktop that I am missing?

Thank you for your help thus far :)

-myk

---

### Post by redilyn on 2009-02-03
TSC should pop back with an error after a period of time. Most likely stating it could not contact the server,

I know you probably did this already but are you sure you changed the protocol to VNC?

Windows uses RDP protocol to do remote desktop, ubuntu uses VNC as far as I know.

Is it possible you turned on UFW on the desktop or any other firewall? If so did you allow port 5900?

Did you change any of the advanced options under System -> Preferences -> Remote Desktop?

Also are you sure you checked the following:

-Allow other users to view my desktop
-Allow other users to control my desktop

I'm at a loss if you have done all of the above. It has always just worked for me....

---

### Post by mykrob on 2009-02-03
Pretty sure I have checked the right settings, I will have to verify when I get home.

Tsclient just reported back, it was unable to contact the VNC server. Does the app have to be reset after each connection, or is it persistent?


Thanks again for your help, I will check the settings and report back later in the day. If you dont mind, please keep an eye on this thread.

later,
-myk

---

### Post by redilyn on 2009-02-03
I will keep any eye out and try to help as much as I can.

I would check to be sure that you didn't check allow local connections only under advanced settings.

---

### Post by mykrob on 2009-02-03
Everything looks good on this end. The display was off when I got home. If power management turns off the display after so long, should this matter?

---

### Post by redilyn on 2009-02-03
Nope, it shouldn't have any effect. When you first connect you might get a black screen but as soon as you start moving the mouse it will show the desktop.

Geez, I never asked, but you tried moving the mouse when you got the black screen right? LoL I'm sure you did :)

And you say you can connect fine inside the lan?

If possible, would you be willing to add this desktop to the DMZ zone on your router to test if you can connect?

---

### Post by mykrob on 2009-02-03
Trying Vinagre from a friend's house now, and I'm getting the error message "Connection to Host ##.#.##.##:5900 was closed. This suggests that now I am at least getting through then getting disconnected immediately.

---

### Post by redilyn on 2009-02-03
Weird, and it never asked for a password?

Can you try TSC again and enter the password before clicking connect

---

### Post by mykrob on 2009-02-03
In TSC, the password block is grayed out. I am able to remote into my router, and I have verified that the port is not blocked, it is forwarded to the correct internal address..

---

### Post by redilyn on 2009-02-03
What version of ubuntu is the desktop that you are trying to connect to running?

---

### Post by mykrob on 2009-02-03
both are 8.10

---

### Post by mykrob on 2009-02-04
It is working now. Not sure why this is happening, but I had the right port forwarded to the right internal address, and it didn't work. I turned on UPNP on the router, and now it works.. Go figure...

Thanks again,
-myk

---

### Post by redilyn on 2009-02-04
Good to hear. sorry for not replying sooner. I just moved and I don't have any computers setup at my new house yet.

Glad you got it working. Strange you had to enable upnp, but hey whatever works!

It may be why it always "just worked" for me, I've always left upnp on for simplicity sake.

---

