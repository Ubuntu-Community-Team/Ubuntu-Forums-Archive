---
title: "HEEEELP!!! How do I get anything to work?!"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by roccoangelo on 2007-07-20
Greetings,

I'm trying to get all the cool looking eye candy effects to work on my Ubuntu install, but nothing I do seems to work. I've used [THIS]("http://ubuntuforums.org/showthread.php?t=488385") walkthrough, but still nothing. Whenever I try logging into Ubuntu using my newly created GNOME & XGL session all I get is screen distortion, as if my LCD's refresh rate is out of wack (though I can log back into a normal GNOME session without any problems). 

Another issue I'm having is that I can't access the ATI catalyst control centre (I'm running a Saphire Radeon 9600 w/256mb or ram and ATI's latest linux driver). I click on it in the ubuntu "start" menu, but nothing happens. 

I've installed both Compiz and Beryl and I can access both of they're control panels, but none of the effects work. Whenever I try to switch to the Beryl manager, any windows I have running will flicker back and forth and then the GNOME default manager will kick in. I can switch to the compiz manager (it looks selected in the menu) but nothing happens. 

I've tried turning on the native desktop effects that are built into ubuntu while I have my video card enabled, but I get some messege about 'composite' somthing or other (I don't have a clue of what it means) and it doesn't work. I thought that Linux was supposed to be more user freindly than this? what's the deal?:confused:

---

### Post by Runamok on 2007-07-21
Hey, I'm a new user too, but please change the title of your forum message. It's helps everyone try to diagnose your problem, if your more specific.    Believe me, I understand your frustration.  I don't know who ever said Linux was user friendly, it's definitely not for the faint-of-heart when your dealing with video card drivers.

From a quick look, you probably have to edit your xorg.conf file.  You can do that by going to the terminal and typing ```
sudo gedit /etc/X11/xorg.conf
```.   Be warned it's dangerous, and you need to make a backup of this file incase you totality butch the X-server.    What is the X-server?  Well, I'm not sure, but it seems to function like explorer.exe.   The X-server is kinda like windows explorer enviroment, and you can make changes to how it loads.  You can even load up different configs of the x-server by hitting F10 ( think) at the log-in screen.  This let you select a graphical failsafe mode.

Please read through following HOW TO: which s to answer you
[URL="http://ubuntuforums.org/showthread.php?t=488385&page=6"]
How To: Compiz Fustion for ATI cards + XGL in Feisty.[/URL]

Need help ask them.

If I remember correctly there is a section near the end of my xorg.conf called "extensions" and it has composite set to on.  Your setup will be different because I am running Beryl with the open-source AIGLX drivers, and your working with Compiz and ATI manufacterer XGL or fglrx supplied drivers.

---

