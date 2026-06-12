---
title: "No Login After Change Of Display Settings"
date: 2009-04-09
forum: General Help
---

### Post by duffboy on 2009-04-09
I have a Dell 710m with an Intel 82852/82855 graphics card.

I recently installed and configured Intrepid Ibex on the system as the laptop is new to me. After getting everything configured just right, I went to hook up my second monitor. I used the GUI's screen resolution settings to set up the second monitor. After putting in all of the settings, I was told to log off and back on.

After I logged off, the screen went to the point where I should be able to log on, but nothing comes up to login.

I am not a Ubuntu newbie, but am a novice and know not what to look for. Frankly, I prefer the GUI over the terminal, I am now ducking to avoid incoming rocks :).

Any help offered would be greatly appreciated as this laptop was supposed to be the first step in my plan to move completely away from Windows and work totally in Ubuntu.

Dave

---

### Post by lavinog on 2009-04-09
can you try **startx**?
also it would help if you can post /var/log/Xorg.0.log

Using the terminal may seem intimidating, but there are alot of things that will be good to know about it.
```

ls lists files
cp copies files
mv moves files
rm removes files
mkdir creates a directory
man gives the manual for a program
cat can output text to the display
less can be used to read text files also (provides scrolling)
sudo lets you execute commands as the super user
dmesg outputs messages from the kernel (handy for troubleshooting)

```
Also pressing tab auto completes the line for you

---

### Post by duffboy on 2009-04-09
lavinog,

Thanks for the reply.

I tried startx and it booted, sort of. After it hung there it gave me an error message saying that User Switcher has quit unexpectedly, at this point I had no mouse or keyboard.

After rebooting, it booted normally. I tried to set the settings again and it did the same thing, I also got out of it the same way.

Perhaps a better question to this problem is, can I have extended desktop with the video driver I am using? How exactly would I go about researching this?

Thanks,
Dave

---

