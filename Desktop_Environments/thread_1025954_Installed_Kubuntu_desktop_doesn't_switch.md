---
title: "Installed Kubuntu desktop doesn't switch"
date: 2008-12-30
forum: Desktop Environments
---

### Post by GuyK on 2008-12-30
I have installed the latest Kubuntu desktop in my installed Ubuntu 8.10.

When I try to switch sessions (Ubuntu to Kubuntu) the best that happens is that I may see the Kubuntu title screen but the system still reverts to Ubuntu desktop. Installation is in an HP Pavilion DV5220 laptop.

Let me know what you still need to know in order to make some sense out of this.

Thanks in advance.

Guy K

---

### Post by Dr.Suave on 2008-12-30
Hope I'm not being too obvious, but have you tried clicking "options" on the login screen? There should be a "change session" or "select session" option or something where you can choose KDE as your environment. Then just type your username and password in the login box like normal, and you should see a shiny new Kubuntu desktop!

If you're configured to login automatically, just press ctrl+alt+backspace while in Gnome (you can do that right now if you like) and you'll be able to log in to KDE following those instructions.

---

### Post by GuyK on 2008-12-30
Thanks for your comment.

Yes, I have done those things in the first paragraph but no shiny desktop results.

As for the auto login, which I guess is operative since I don't have to log in, ... I'll have to try that. I have to come out into windows in order to get on line cuz, among the problems I'm working through, I am not making headway in getting my dial up connection to work--yeah, I'm still stuck with dialup. It's a bummer! I will try the toggle that you suggest. Maybe that will work.

Thanks again.  Talk to ya later.

---

### Post by Dr.Suave on 2008-12-30
For sorting out dial-up in Kubuntu (and it will probably work in Ubuntu too as long as you've installed Kubuntu) press alt+F2, type kppp, and press enter. (or have a look at [http://www.kubuntu.org/docs/kquickguide/C/ch02s06.html](http://www.kubuntu.org/docs/kquickguide/C/ch02s06.html))

---

### Post by GuyK on 2008-12-31
Re KDE Desktop:

The CTRL-Alt-BS toggles as you suggested but to a login panel in what I take to be the gnome colors. When it settles it is back in Ubuntu. Toggling again just repeats the sequence. Never see the KDE desktop.

RE the KPPP issue:

I probably need to do some searching the threads. The short story at the moment is ... I have expereince with KPPP in a couple other linux systems. This one is a bit flakey. I have it configured OK. Sometimes when I connect it replies immediately that it can't find the modem (ttyUSB1). Other times (possibly more often) it initializes the modem, dials and goes to CONNECT. Then it dies. In the CLI screen I see a couple of lines possibly suggesting the problem: "ppp daemon died suddenly," "error opening resolve.conf," "pppd died." 

One basic question you might answer for me: I would like to use the redirect operator (>) to capture the streams of data on the CLI screen. I haven't got the experience to know what what command results on the screen can end up in a capture file and what will not. I try to capture error messages and then find some of the files empty. I would like to be able to document my problems as fully as possible but I donn't think that it is fun to try to transcribe a screen or more of data by hand. There is probably a trick or two that I have to learn.

Thanks for enduring this!

Happy New Year!

Guy K

---

### Post by Dr.Suave on 2008-12-31
CTRL+ALT+BS gets you to the login screen. At the login screen, in the bottom left hand corner you can click on "options", then from the popup menu that appears, click "select session", then check the radio button next to "KDE". Then login - once you've given the right username and password, the system will give you the option of making KDE default, or just using it for this session only. It's your decision.

I might have misunderstood the problem, so forgive me if I just gave ridiculously simple instructions, but I reckons it's best to start with the easiest solution.

If that doesn't work, there's [COLOR="Blue"][this guide here]("http://www.ubuntugeek.com/how-to-install-kde-41-on-ubuntu-810-intrepid-ibex.html")[/COLOR], but as long as you have managed to install the kubuntu desktop, you shouldn't need it.

Sorry but I don't know about your pkkk problem.

---

### Post by GuyK on 2008-12-31
I have tried faithfully to do exactly what you described here.

It only opens gnome desktop sessions.

Do you have a suggestion as to what I do next?

I appreciate your efforts.

Guy K

---

### Post by Dr.Suave on 2008-12-31
That's a pain in the bum - the thing I would do next is just try doing things like reinstalling the kubuntu desktop with sudo apt-get install kubuntu-desktop, and maybe re-posting the problem in a more happening sub-forum - desktop environments doesn't seem to get much attention, and my ability to help is pretty limited by the fact that I'm relatively new to Linux.

Good luck!

---

### Post by GuyK on 2009-01-02
Reinstalling has not accomplished anything.

Can you (or anybody else) make a suggestion as to a "more happening sub-forum" where it might attract attention?

Guy K

---

