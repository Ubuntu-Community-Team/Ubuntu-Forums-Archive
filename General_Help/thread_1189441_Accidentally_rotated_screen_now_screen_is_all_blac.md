---
title: "Accidentally rotated screen now screen is all black"
date: 2009-06-16
forum: General Help
---

### Post by dumbnumpty on 2009-06-16
I really hope someone can help with this.

I accidentally clicked the display applet (which I don't seem to be able to find right now :/ ) which rotated my screen display.

Now the screen is all black except for the cursor which I can still see. This change has only been applied to *my* account - all of the others are fine.

What I can't find are the user-specific display settings to edit to get things back to normal. Everything I've found seems the same from session to session.

Where does gnome-display-properties write to? How can I revert the rotation setting?

Thanks.

---

### Post by days_of_ruin on 2009-06-16
So have you restarted the computer?

---

### Post by dumbnumpty on 2009-06-17
I've restarted several times since this first happened. Every time I try to use my main profile, the same thing happens. The display is rotated (I can tell by the angle and position of the cursor) and it's completely black. I'm having to log on using my girlfriend's profile and use the Guest account to post this message.

---

### Post by OneNite on 2009-06-24
Hey, I just ran into this problem myself just now, and after spending some time looking in the 'home/*youraccount*/' directory, I was able to find the file that held the display settings for your account and was able change it back to normal.

Here's how to do it:
1. In someone else's account, open a terminal and type in 'sudo gedit /home/*youraccountname*/.config/monitors.xml'
2. Look for the line where it says: '<rotation>*currentrotatrion*</rotation>' and replace 'currentrotation' with 'normal'

Hope this helps!

---

