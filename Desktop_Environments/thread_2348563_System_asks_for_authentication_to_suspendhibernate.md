---
title: "System asks for authentication to suspend/hibernate"
date: 2017-01-04
forum: Desktop Environments
---

### Post by chazzyfresh33 on 2017-01-04
I switched back to Xubuntu today, and it's working exactly the way I want it to save for one thing. I have my Power Manager set to Suspend both on Battery and when Plugged in after 15 and 25 minutes, respectively. However, I noticed when I had it plugged in, a dialog asked me to authenticate before the system would suspend after I woke the system back up. I fixed this by applying the tip described here: [https://askubuntu.com/questions/543921/authentication-required-before-suspend#700713](https://askubuntu.com/questions/543921/authentication-required-before-suspend#700713)
I decided to test on battery to be on the safe side, and was disappointed to find that the same thing was happening, with one major difference: The dialog now asks me to authenticate in order to Hibernate. This is confusing to me because not only is Suspend my chosen method of sleep mode, but Hibernation is not even enabled on my system due to the damage it can potentially do to SSDs. 
Does anyone know how to rid myself of this dialog and ensure that the system is suspending as opposed to hibernating?
Thank you!

---

### Post by egeezer on 2017-01-06
All I can think of is that you might check in Synaptic to make sure uswsusp is installed.

---

