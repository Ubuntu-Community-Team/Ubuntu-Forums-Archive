---
title: "How to remove the annoying Unity/ netbook environment"
date: 2010-11-11
forum: Desktop Environments
---

### Post by quantumcat on 2010-11-11
Hi Guys,

I found a way to remove the panels and go to the normal setup in 10.10.

It took me a while to find a solution so I thought Id share the information

Credt to original writers

QC



> [CENTER][LEFT][COLOR=#333333]You   should be able to go to the login-screen manager and select to start in   "Ubuntu Desktop Edition" instead of "Ubuntu Netbook   Edition" as default there.[/COLOR][/LEFT]
[/CENTER]
[LEFT]
   [/LEFT]
[CENTER][LEFT][COLOR=#333333]It   is available under the System menu, however as I'm using the Dutch   translation of Ubuntu the exact name of it in English or other languages is   unknown to me. Hope this helps regardless :-)[/COLOR][/LEFT]
[/CENTER]
[LEFT]
   
   [/LEFT]
[CENTER][LEFT][COLOR=#333333]You   can also change which desktop environment you start in per session. Just   click your username in the login screen, then in the lower half of the screen   should be a session selector which defaults to "Ubuntu Netbook   Edition". Change it to desktop and you're ready to go.[COLOR=#005151][FONT=Verdana,Arial,Tahoma]
[/FONT][/COLOR][/COLOR]

[COLOR=#333333]Note   that this all does not "remove" the Netbook Edition, but merely   disable it though. The proper procedure is probably to remove the installed   packages for it.[/COLOR][/LEFT]
[/CENTER]
           [COLOR=#666666]
[/COLOR]
> [COLOR=#666666]Follow the steps below to [/COLOR]**[COLOR=#333333]remove Unity from your Ubuntu 10.10 to return to classical UNR[/COLOR]**[COLOR=#666666] with large application windows, no need to downgrade your entire OS to change desktop environment. The general idea: install ubuntu-desktop, delete the unity and anything related with ubuntu-netbook, and then make use of the maximus software to enlarge your application window. [/COLOR]
  
[LIST=1]
[*]Run:      apt-get install ubuntu-desktop
[*]Exit      from the netbook session (logoff), log into Ubuntu deskop session, and      then delete following software:
     apt-get --auto-remove purge unity*
     apt-get --auto-remove purge ubuntu-netbook-default-settings
     apt-get --auto-remove purge compiz*
     apt-get install maximus
     apt-get --auto-remove purge mutter*
     Note: Of course you can write them in a line, here just for you to see      clearly. As for Compiz, you can delete it as you like, I think it is of      little value.
[*]Run      gnome-session-properties, add in maximus.
[*]Logoff,      log on (still log into the desktop session).
[*]Change      desktop environment:
     Remove some panels and applets, and then add some special applets:      window-picker-applet, Indicator Applet and Indicator Applet Session.
[/LIST]
  [COLOR=#666666]The interface now compared to the classical UNR interface, it only lacks a menu display controlled by ubuntu-launcher. Maximus's role is to maximize the open applications, if some applications are not suitable to adjust by the maximum, you can look for the maximus in *[FONT=Calibri]gconf-editor[/FONT]*, then to set it. 

In addition, I recommend you to install the latest official verified graphics drivers (for example, [ATI Catalyst 10.10]("http://www.*****************/driver/articles/amd-catalyst-10-10-8-872-download-for-ubuntu-10-10.html"), [Nvidia Forceware 260.19]("http://www.*****************/driver/articles/latest-nvidia-video-drivers-260-19-12-download-for-ubuntu-10-10.html")) from AMD/NVIDIA website. The default graphics drivers from Ubuntu may have disable some functions (which makes the desktop effects can't work) for special perfermance enhancement.[/COLOR]


---

### Post by kerry_s on 2010-11-11
all you have to do is log out & select "ubuntu desktop edition" in the session menu.
you do not need to install anything or remove anything.

the standard desktop has always been included on every netbook version.

---

### Post by quantumcat on 2010-11-11
It took me as a noob a while to figure it out lol

---

### Post by sophontteks on 2010-11-11
oh thank god this side panel reminds me of a tumor. Seriously, I want to punch my screen because it is so annoying!!!!
Too bad there isn't a way to downgrade the os back to the way it was before.
Is there a way to add the main menu into the background manually? That was my favourite feature from before. Fast, simple, easy to read, and good-looking. This side panel..ugh...10.10 netbook is the windows vista of netbook OSes if you get my drift.

---

### Post by kerry_s on 2010-11-11
> **sophontteks said:**
> oh thank god this side panel reminds me of a tumor. Seriously, I want to punch my screen because it is so annoying!!!!
Too bad there isn't a way to downgrade the os back to the way it was before.
Is there a way to add the main menu into the background manually? That was my favourite feature from before. Fast, simple, easy to read, and good-looking. This side panel..ugh...10.10 netbook is the windows vista of netbook OSes if you get my drift.

install "netbook-launcher-efl" then log out & select the netbook 2d in the session menu, that will give you the look of ubuntu 10.04.

unity's not bad, just takes getting use to. i'm using it.

---

### Post by sophontteks on 2010-11-11
Ah thank you I'm already working on that now actually. I don't want to waste any more CDs on operating systems today.
I really did not like KDE's netbook plasma idea either, which is what I tried before ubuntu netbook.

On a more positive note I just wiped mandriva from my system after a year of terror(no matter how many problems I fixed more would pop up). I am very happy with kubuntu, which wasn't too difficult to setup with my dreaded GMA500.

MY girlfriend's laptop is a mite smaller then my own, and the saved screen space in the old system was a blessing. I just cannot have a big side panel taking up so much of the screen.  Netbooks aren't made to run many applications at once anyway, so the idea around this eludes me. Besides it could all be fixed  if I could set it to auto-hide.
In fact that was one reason I was  so ticked off after(literally) 10 minutes. I right clicked 50 times, looked through all the different customising tools, and searched on the Internet just to finally learn that I cannot change anything about the side panel at all!

I also had some problems with the shortcut menu in the new version. The old menu had tabs on the left side, which I would click, and it would show me applications in that catagory. While the new menu is just random, Not all the categories are shown, I click Internet, and firebox opens (why didin't you just call it firefox then!) I could not find  a way to customize these menu's either. very unfriendly in my opinion.
I also prefer how the old system was always on the desktop. that's one less mouse click.

Oh furthermore all those  neat little widgets .setup for social networking are far too memory intensive for many netbooks. Every time I switched desktops the system froze for a few minutes.
IF your going to keep that I would suggest that a benchmark is done during installation, and if the netbook isn't fast enough the installer skips this option. It would also make sense that the account settings were completed during installation as well, so that everything runs all nice a pretty right out of the box.

---

