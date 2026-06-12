---
title: "Any application gets foreground"
date: 2008-01-10
forum: Desktop Environments
---

### Post by blackeyeddog on 2008-01-10
There's a behavior of my Gnome Desktop Environment that I would like to change, but I don't know if it's a fixed built-in or can be disabled or improved in some way.

I use Gutsy Gibbon at work, and accept as normal that some applications take a long time to open. So I start them and keep working in another application, until they get loaded. Normally this "application ready status" is preceded by 1 or 2 seconds with all applications freezing.So far, so good.

What happens is that any application,when it concludes its loading / initialization process, robs the attention, getting the foreground. This is not only annoying, but sometimes implies in security risks, as I tell in these two real-life examples :

- attending a user at my desk, I was logging as root in a corporate AIX server when the box froze for that 1 or 2 seconds, and then an Open Office spreadsheet, that I opened 1 minute before, popped up and showed the password plainly.

- yesterday I was typing an e-mail about a fire detector, and when typing a line ending with "alarm procedures", guess what, machine froze a little and Gnome terminal opened seconds before popped up getting exactly "rm procedures<ENTER>" , removing a text file called "procedures". No kidding, this really happened, and it's what convinced me to post for help..

Does anybody knows if this foreground overtaking behavior can be disabled ? Or at least defined in an individual application basis ? 

Sorry if this is a silly question, but I searched for hours in this forum and the Internet, and could find nothing about the subject. I started using Ubuntu/Gnome intensively only one year ago, before that it was not a concernment. Maybe it's a very basic thing, a normal and unavoidable feature of Linux kernels or Desktop Environments. Thanks for any answer.

---

### Post by blackeyeddog on 2008-01-17
Just for closing the thread : I found in  a Gnome forum that this behaviour is normal , it's a deficiency of Metacity, the Windows Manager used as default in Ubuntu 7.10 . People workaround it by using devilspie or installing some other Windows Manager.

---

