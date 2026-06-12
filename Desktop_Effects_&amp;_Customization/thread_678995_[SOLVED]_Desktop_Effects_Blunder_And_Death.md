---
title: "[SOLVED] Desktop Effects Blunder And Death"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by widowmaker on 2008-01-26
Hello Everybody,

I am here once again because I like to experiment to much and can't leave well enough alone. Anyway live and learn as they say. So let me begin.

[COLOR="Blue"]THE COMPUTER:
Compaq Evo N1015v Laptop
1.2 GHz processor
512 MB RAM
30 Gig HD
Dual booted with XP and Ubuntu 7.04[/COLOR]

[COLOR="Red"]THE PROBLEM:[/COLOR]
This morning I just got done getting Ubuntu 7.04 all updated and all setup just the way I wanted it and even installed some new themes along with my old standby themes. After completing these tasks, I was going through the System>Preferences menu and came across the Desktop Effects and opened it up. It contained 2 check boxes for wobbly windows and workspace on a cube. Not paying attention at what was checked I had a leap before you look moment and pushed the Enable Desktop Effects button. I knew at an instant I just screwed up (GUT FEELING), and I did.

After pushing the enable button the program started to work then it blinked a couple of times and then nothing. The whole computer froze up, I couldn't do anything. So thinking that maybe it was still working and processing, I waited almost 2 hours and finally cold booted it after coming to the conclusion that nothing spectacular was going to happen.
[COLOR="Red"]
UPON REBOOT THIS WHAT HAPPENS:[/COLOR]
The laptop loads through the Ubuntu Orange Bar
It blinks the screen twice and
Then I end up with a grey and blue screen that says: 
" Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? "
So the view shows a bunch of computer language most of it gibberish to me then it comes up with " The X Server is now disabled. Restart GDM when it is configured correctly." Then you push ok and it goes back to the check list that it was going through when loading. The last entry shown is " loading local boot scripts" (/etc/rc.local)

[COLOR="Red"]CONCLUSION:[/COLOR]
Thats it either reboot it and it goes through the same thing or shut it off. I need to know how to roll back and disable Desktop Effects and get proper bootup to occur before I bite the bullet and reinstall. Reinstall is easy. I want the challenge of fixing it. After all that is how I learn, and that is the fun of Linux, especially Ubuntu.

I will warn you that I am not to spectacular on the command line stuff, but I am able to stumble through it with good guidance and direction.

Any help will be appreciated greatly as it would save me the 4 to 5 hours of reloading and getting everything back the way I want it. SO,[COLOR="DarkOrange"] I am thanking you in advance.[/COLOR]
[COLOR="Purple"]
My apologies if this isn't in the right section. Administrators please feel free to move it where necessary. I just figured Desktop Effects are what caused my problem this would be a good starting spot.[/COLOR]

---

### Post by overdrank on 2008-01-27
HI and you can try and boot into recovery mode which is usually the second choice in the grub. The reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` or startx, hopefully this will get you to a GUI, Desktop. Good luck.

---

### Post by widowmaker on 2008-01-29
Hey Overdrank,

Thanks for the suggestion, but I will have to try it out next time as I resolved this issue myself with a reload of 7.10. Got tired of waiting for a response and I had some time to kill on Sunday. Up and running again. Thanks for responding all the same.

---

