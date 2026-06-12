---
title: "NO Sound on Dell Zino HD???"
date: 2011-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by medzeppelin on 2011-06-26
[SIZE=2]Hello, I'm new to Ubuntu 11.04.  I installed this in my Dell Inspiron 400 Zino HD.  Unfortunately, I have no sound.  I used terminal to find my sound card:

 **ATI Technologies Inc RS780 Azalia controller**

Can anyone walk me through how to correct this matter?  

Thank you...[/SIZE]

---

### Post by martinh78 on 2011-10-14
Hi,

Not sure if this is too late to help you or if you already discovered the answer, but here's how I got HDMI audio working in 11.04 on a Dell Zino HD:

First up, I did the following in a PenDrive install of Linux, so if it all went wrong it didn't matter - if you're doing it live, be sure to make appropriate backups.

In order to get HDMI Audio working you'll need the proprietary ATI drivers. To get them, type the following command into a console (press ctrl+alt+t to get a new console):

[FONT=Courier New]sudo apt-get install fglrx  [/FONT]

[FONT=Arial]This may [/FONT]take a little while to install.

When that has finished, again in the console type:
[FONT=Courier New]
sudo aticonfig --initial -f[/FONT]

[FONT=Arial]Now reboot your machine.

Once rebooted go to Menu (the icon in top left of the screen) > System Settings > Sound

On the Output page select the RV710/730 option. Go to the Hardware page and select the RV710/730 option and click test speakers. All being well sound should now be working over HDMI!

Cheers,

Martin.
[/FONT]

---

### Post by LEdesigns on 2012-04-20
Thanks Martin!

Your tutorial worked great!


I also found a tip to use the front sound jack (the rear jack doesn't seem to work for Ubuntu).  You'll need to change the sound settings to go back to analog if you followed Martin's instructions.

---

