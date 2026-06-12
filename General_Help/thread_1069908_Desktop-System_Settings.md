---
title: "Desktop-System Settings"
date: 2009-02-14
forum: General Help
---

### Post by xtiano77 on 2009-02-14
Issue #1: 

I downloaded the "desktop settings" program and when I try to use it, it shows me the following message:

The shared librarywas not found.Library "kcm_kwindesktop" not found"

Possible reasons:

     * An error occurred during your last KDE upgrade leaving an orphaned control module
     * You have old third party modules lying around.




Issue #2:

Also, I have a two monitor setup. Monitor #1 is where both system bars show up.  That monitor is an ACER 191W.  Monitor #2 is to the right of Monitor #1. That monitor is an ACER 193W.  I just purchased another ACER 193W and switched with the Monitor #1.  Everything works fine once I am logged into the system, but while the system is loading, it seems as if the system still applies the settings of the old Monitor #1 to the new one. Is there a way to have the system check both monitors and recognize the new monitor so it won't apply the old settings to the new one?  As always, thanks in advance for your help.

---

### Post by porksome on 2009-02-15
I have exactly the same problem after upgrading to kde 4.2 on intrepid. I have no window borders or keyboard control.

Anyone know which modules need to be installed or removed to fix?

Thanks

---

### Post by rjs987 on 2009-02-23
I also have that same problem on my test system at work - same as xtiano77 issue #1 and same as porksome. I even tried the virtual keyboard but still no input from that either. This happened after a series of updates and then a reboot. Now there shows to be 13 more updates found at this time and no way to type in the admin pw to install those.

On my home system I was having some issues with the recent updates but didn't loose keyboard control and was able to get the last updates installed and do another reboot. Now my home system is working nicely. But my work system is a big problem (especially since my work place primarily uses MS products and Linux users are not looked on favorably. This adds fuel to 'their' fire against us).

---

### Post by rjs987 on 2009-02-24
BUMP.
Just wondering if there is any help for this issue?
kcm_kwindesktop missing and no keyboard control once into KDE and no window borders on apps I can open with the mouse (including no title bar at the top of the app window). I can login to the console from the login screen (or using ctrl-alt-f1) without going to KDE but then I don't know what to do from there to restore the window manager or keyboard within KDE.
Any help please?

---

### Post by rjs987 on 2009-03-04
Well, I finally fixed the problem of no window borders and no keyboard control. 
Initially, since I still had mouse control and I also have a link to a shared drive on another machine I put a text file with my password there and just opened the text file from the bad machine. I was thinking that if I could just get the pending packages and updates to install the problem would be fixed. There were still 13 updates pending but I couldn't type the admin password in to run the updates so I was thinking I could cut and paste the password from the text file to get there. That did work as intended, and the updates did install, but that didn't fix the problem. kcm_kwindesktop was still an orphaned module. But I'll remember this attempt for some future flaw that may possibly happen.

I was going to just reinstall, but didn't want to mess up the settings I already had. It then occurred to me to just reinstall KDE. But how to do this if I can't type commands, or even copy and paste them into terminal. So I logged into the root console as I mentioned about earlier (I can type commands there since that is outside KDE) and did all I needed to from there.
(for newbies like me)
First I entered my username and password to go to the prompt.
Then
```
sudo -s -H
```
followed by my password to gain root.
Then
```
apt-get install kde
```
to reinstall KDE.
And finally
```
reboot
```
to restart the computer.

When I logged in to KDE all was working as it should. Window borders were back and also keyboard control, even my keyboard shortcuts as I had them configured. So this one is solved for me.

What did you do to solve it? I'd like to know.

---

