---
title: "automatic login built-in guest account"
date: 2011-12-08
forum: Desktop Environments
---

### Post by poevold on 2011-12-08
I'm trying to figure out how to login automatically to the built-in guest account on ubuntu 11.10. The reason why I want to login to the guest account is because I have this computer for public use. Whatever my klients save on the computer it must be erased when computer restarts. All for my clients safety. Or is there another way to do it? I new in this ubuntu world, so hopefully some one could help me! :)

---

### Post by PatrickD-52761 on 2011-12-30
> **poevold said:**
> I'm trying to figure out how to login automatically to the built-in guest account on ubuntu 11.10. The reason why I want to login to the guest account is because I have this computer for public use. Whatever my klients save on the computer it must be erased when computer restarts. All for my clients safety. Or is there another way to do it? I new in this ubuntu world, so hopefully some one could help me! :)

This might get you started. It's about setting Ubuntu up as a Kiosk.  Although it might not solve the problem of erasing the files, but I'm sure that's covered somewhere.

Here's the link: [http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/")

This looks even more promising for you: [http://www.howtogeek.com/59839/how-to-reset-any-changes-to-your-ubuntu-computer-and-add-kiosk-mode/]("http://www.howtogeek.com/59839/how-to-reset-any-changes-to-your-ubuntu-computer-and-add-kiosk-mode/") It's an application that restores the home folder and other settings on reboot, and also discusses how to set Ubuntu up as a kiosk. ***Note, I haven't used any of these methods***

Hope these help, and have a great weekend:)
Patrick.

---

### Post by zeroconf on 2012-01-14
> **PatrickD-52761 said:**
> Here's the link: [http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/")

I need to use Firefox, because my country's ID-card doesn't work with Google Chrome. This is poor solution anyway, because there is needed to use all other application in the computer, not just web browser.

> **PatrickD-52761 said:**
> This looks even more promising for you: [http://www.howtogeek.com/59839/how-to-reset-any-changes-to-your-ubuntu-computer-and-add-kiosk-mode/]("http://www.howtogeek.com/59839/how-to-reset-any-changes-to-your-ubuntu-computer-and-add-kiosk-mode/") It's an application that restores the home folder and other settings on reboot, and also discusses how to set Ubuntu up as a kiosk.

ofris doesn't work on newer Ubuntu versions than 10.10. It works mostly at XFCE but not at Gnome or KDE based versions of Ubuntu. There isn't unfortunately no other application similar to ofris funtionality.

So, the guest account automatic login is still needed. But [askubuntu.com has one solution]("http://askubuntu.com/q/95405/41929") - this needs to be tested...

---

