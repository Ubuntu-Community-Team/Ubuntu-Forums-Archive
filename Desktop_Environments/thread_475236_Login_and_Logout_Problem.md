---
title: "Login and Logout Problem"
date: 2007-06-15
forum: Desktop Environments
---

### Post by Karusune on 2007-06-15
I am very new to the linux community and I have recently installed Ubuntu Fiesty Fawn onto my computer, it is a dual boot where Windows XP is currently running on the primary disc drive and Ubuntu is running on a secondary. I have had it installed for about two days, and up until yesterday I have had absolutely no problems.

Yesterday, I tried to log off since I created an account for my little brother, and it just stayed at a blank screen after logging off, so I had to shut it off and turn it back on to log-in. Well, I had just recently installed the Kubuntu-desktop since a friend of mine suggested that I do so since it is supposed to be "easier" for a windows user to get used to, and now that it is installed, I cannot log into my account at all no matter what session I am using. Neither KDE nor Gnome will log-in, when I put in my information it accepts it, but it goes to a blank screen.

Does anyone have any ideas as to what the problem could be? If this is a simple problem, I must sincerely apologize as I am still learning how to use Ubuntu and other forms of Linux, I have always used Windows (a little bit of mac) so I have no experience with working with the terminal and such, though I know how to use some of it (such as sudo.)

Thanks for all of the help and I really appreciate what you are all doing here, and I would like to thank the Ubuntu team for the hard work and determination.

---

### Post by dbbolton on 2007-06-16
> **Karusune said:**
> I am very new to the linux community and I have recently installed Ubuntu Fiesty Fawn onto my computer, it is a dual boot where Windows XP is currently running on the primary disc drive and Ubuntu is running on a secondary. I have had it installed for about two days, and up until yesterday I have had absolutely no problems.

Yesterday, I tried to log off since I created an account for my little brother, and it just stayed at a blank screen after logging off, so I had to shut it off and turn it back on to log-in. Well, I had just recently installed the Kubuntu-desktop since a friend of mine suggested that I do so since it is supposed to be "easier" for a windows user to get used to, and now that it is installed, I cannot log into my account at all no matter what session I am using. Neither KDE nor Gnome will log-in, when I put in my information it accepts it, but it goes to a blank screen.

Does anyone have any ideas as to what the problem could be? If this is a simple problem, I must sincerely apologize as I am still learning how to use Ubuntu and other forms of Linux, I have always used Windows (a little bit of mac) so I have no experience with working with the terminal and such, though I know how to use some of it (such as sudo.)

Thanks for all of the help and I really appreciate what you are all doing here, and I would like to thank the Ubuntu team for the hard work and determination.
is it possible that you have run out of disk space?

---

### Post by shadows85 on 2007-06-17
> **dbbolton said:**
> is it possible that you have run out of disk space?

I sort of doubt that since I have the same problem and I still have about 190 GB of unused space..

---

### Post by dbbolton on 2007-06-17
> **shadows85 said:**
> I sort of doubt that since I have the same problem and I still have about 190 GB of unused space..
boot into recovery mode and run this command

```
cat /home/YOUR USERNAME/.xsession-errors
```

---

