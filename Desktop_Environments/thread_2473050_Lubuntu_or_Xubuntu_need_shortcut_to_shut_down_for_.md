---
title: "Lubuntu or Xubuntu need shortcut to shut down for elderly individual"
date: 2022-03-22
forum: Desktop Environments
---

### Post by jmichaels29 on 2022-03-22
When using either Lubuntu or Xubuntu, I need a shortcut to shut down, the computer, an for elderly individual - my 81 year old Aunt.

After installing a new battery for the laptop & a SSD (both arriving tomorrow), I will be installing either Lubuntu or Xubuntu on her aging laptop (specifically the HP 2000 Notebook PC model).

I will be stream lining the system so that it does only what she needs; for example. the system will boot up and automatically open the browser and automatically log into Facebook for her - I have all that figured out.

I would like to figure out a very easy way, for whichever OS I settle on, to have a very *very* easy way to shut down the computer when it's finished being used.

The ultimate solution would be to have some type of shortcut on the desktop, that she could double click and it would just shut down - I know this may not be possible though.

What suggestion(s) would users here have to make shutting down the system the easiest.  

I have not fully explored either OS, although I did create a bootable thumb drive and played around with each.  Either OS is acceptable. 
 
I haven't tried it, but perhaps if she simply pushed the on/off button on the laptop, it would force one, or both, OS to go into a shutdown mode (or ask if she would like to shutdown/restart as Ubuntu LTS once did) - ?
 
Also, perhaps there is some programming code I could enter into terminal that would arrive at a solution? 
 
Much thanks in advance for all consideration and suggestions! 
 
 
Regards,

MJ

---

### Post by TenPlus1 on 2022-03-22
You could always configure the power button to simply shut down the laptop when pressed, that way it turns things on and closes things down without issue.

---

### Post by jmichaels29 on 2022-03-22
> **TenPlus1 said:**
> You could always configure the power button to simply shut down the laptop when pressed, that way it turns things on and closes things down without issue.

Ok then.

I just booted Xubuntu from the thumb drive, on my desktop, and simply pushing the power button, it forces the computer into asking if one wants to shut down.  I think this will be good enough.
 
However, if there is a way to simply push the power button and have it automatically shut down, that would be even better!
 
I have no programming/coding skills, so if anyone could tell me how to pull this off - either via GUI clicking around or via entering things into terminal, that would be very good.
 
Regards,

MJ

p.s. Does Lubuntu also bring up a screen with the option to shut down when the power on/off button is pressed?

---

### Post by guiverc on 2022-03-22
Yes I've used the POWER BUTTON to shutdown both Lubuntu & Xubuntu.

However I don't believe it will work on all hardware; as I've used boxes with the same setup where it doesn't work, but turns off perfectly on other boxes. If it works with Xubuntu - I'd expect the same with Lubuntu (again if it doesn't work with Xubuntu I'd expect the same behavior with Lubuntu).

For Xfce (Xubuntu) there is a `xfce4-session-logout` command which can make the system logout (with options to suspend, hibernate, etc.

For LXQt (Lubuntu) there is `lxqt-leave` which has options to suspend, hibernate, shutdown etc... 

You've not provided release details; so adjust for your *unstated* release  (I used `man` (*which shows the manual page on the terminal*) on my release to look up options as I know some vary on release)

Addendum:  Sorry this response isn't very *newbie* friendly;  the obvious places I'd look are the [manual]("https://manual.lubuntu.me/stable/3/3.2/3.2.14/shortcut_keys.html") though in the case of shortcuts I'd read Walter's answer at [https://discourse.lubuntu.me/t/where-can-i-program-shortcuts-in-lubuntu-20-10/1837/2](https://discourse.lubuntu.me/t/where-can-i-program-shortcuts-in-lubuntu-20-10/1837/2)

Do note:  The manual URL can vary for releases; eg. [https://manual.lubuntu.me/stable/3/3.2/3.2.14/shortcut_keys.html](https://manual.lubuntu.me/stable/3/3.2/3.2.14/shortcut_keys.html) was used in this case, where *stable* will show the *latest* *stable* release which currently is Lubuntu 21.10.  Just replace the word "*stable*" in that URL with "*lts*" to view the *latest lts* version of the manual; ie. currently that's Lubuntu 20.04 LTS.  In the Lubuntu discourse post; Walter was talking about 20.10 which was the *latest stable* release at the time, thus why that link was used.

*To answer properly needs a starting point, at least for me - which requires a known release. Software changes over time with more options being added, some being taken away - so if we reply without knowing the release the answer may not work for you...*

---

### Post by oldos2er on 2022-03-22
> **jmichaels29 said:**
> Also, perhaps there is some programming code I could enter into terminal that would arrive at a solution?

No idea about programming code, but there is a command you could create an alias for ```
sudo shutdown -h now
```

---

### Post by bobunderwood99 on 2022-03-22
Hello,

Xubuntu 20.04: open Power Manager, select "Shutdown" under "When power button is pressed:"

Lubuntu 20.04: open Power Management (Preferences>LXQt settings). You can set to shutdown on lid closure or idle time.

+1 for Xubuntu.

---

### Post by GhX6GZMB on 2022-03-23
Lubuntu:
1: open the "Leave" menu.
2: drag the "Shutdown" icon onto the desktop.
3: right-click the new icon.
4: tick "Trust this executable".
Done.

+1000 for Lubuntu. ):P

Why make things complicated?

---

### Post by ajgreeny on 2022-03-23
For many years now I have used the Pause/Break key on my Xubuntu systems linked to the ***xfce4-session-logout -suspend*** command  mentioned above by guiverc to immediately put the computer into suspension or ***xfce4-session-logout -halt*** linked to Pause/Break + Winkey to immediately shutdown the system.
No confirmation for either action is needed; just hit the key or keys and it happens immediately.

---

### Post by GhX6GZMB on 2022-03-23
> **ajgreeny said:**
> For many years now I have used the Pause/Break key on my Xubuntu systems linked to the ***xfce4-session-logout -suspend*** command  mentioned above by guiverc to immediately put the computer into suspension or ***xfce4-session-logout -halt*** linked to Pause/Break + Winkey to immediately shutdown the system.


Right... super-intuitive for an 81-year old lady.

---

### Post by ajgreeny on 2022-03-24
> **ml9104 said:**
> Right... super-intuitive for an 81-year old lady.
I'm not sure if that is meant sarcastically or not, but if it is, then why is it not at least as good as any other quick method of shutting down.

Use of the Pause/Break key which is no longer used in most OSs seems pretty reasonable to me.  If the elderly person wants to always shutdown and not suspend you could use the Pause/Break key on its own to shutdown instead of suspending by simply changing the linked command.

PS:
I'm not too far away from 81 years old and I don't find such things difficult to set up, which you seem to be suggesting is the case.

---

### Post by ActionParsnip on 2022-03-25
If you add in visudo that shutdown can be ran with sudo with no password then you can set a button on the keyboard to run the command and shutdown the OS

---

