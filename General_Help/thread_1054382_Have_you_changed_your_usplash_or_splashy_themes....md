---
title: "Have you changed your usplash or splashy themes..."
date: 2009-01-29
forum: General Help
---

### Post by grndslm on 2009-01-29
Have you changed your usplash or splashy themes with Intrepid??

I've been using startupmanager to TRY to change my usplash theme, but it never works... the only one that works is the default ubuntu usplash theme with the orange bar.

I've also used startupmanager with splashy to use a splashy theme I created with "splashy_config -c".  My custom theme with splashy ALMOST works.  At boot, it spits out some splashy error (-3), and then it flashes my startup.jpg, then goes back to text, then goes to the startup.jpg for a little more than 5 seconds, and then it goes back to the text again.  Shutdown works great, but I'm not sure what's happening with the startup.

If anybody has sucessfully customized their boot splashes with Intrepid... I'll be glad to listen to any advice and/or steps taken to do so.  I've tried multiple ways, multiple times... and it just doesn't work.  And I think using startupmanager on my laptop has caused it to freak X server out.  Seems like the first boot of the day is the only one where X is displayed properly... all other boots always look like a funky X (messed up colors, double vision, missing chunks of the display altogether, etc.)

I know I've changed usplash before with previous releases... and it was never this hard.  Somebody please help.

---

### Post by dcstar on 2009-01-29
> **grndslm said:**
> 
........
I've also used startupmanager with splashy to use a splashy theme I created with "splashy_config -c".  My custom theme with splashy ALMOST works.  At boot, it spits out some splashy error (-3), and then it flashes my startup.jpg, then goes back to text, then goes to the startup.jpg for a little more than 5 seconds, and then it goes back to the text again.  Shutdown works great, but I'm not sure what's happening with the startup.
.......

Any time usplash resolution changes are made you have to do the following, I would imagine it also applies to other changes:

```
sudo update-initramfs -k all -u
```

---

### Post by grndslm on 2009-01-30
OK... so, I've finally gotten my custom splashy theme to work a bit better.  It doesn't flicker anymore (that was the fade feature that "splashy_config -c" uses by default), but it still gives me this stupid error for about 5 seconds on boot:

Splashy ERROR: Connection refused
Splashy ERROR: Couldn't splashy_start_splashy(). Error -3 

... and then it shows the bootup image I use in my theme just fine.

Why does it keep displaying this error and then go on to display my bootup image??  I'm guessing it has something to do with initrd... but I'm not an expert in any of this stuff.

Again... any advice would be great.

---

### Post by grndslm on 2009-02-02
Just for anybody that cares... I think the -3 error I was getting with splashy was due to me using .JPGs instead of .PNG images.  Hopefully that error will be gone when I get a chance to restart.

As for usplash, I finally found 2 themes that worked "chrome-new" and the fingerprint theme, which I had to compile myself.  Other than that... something major must have been rewritten in usplash, breaking functionality of all other themes.  St00pit!

---

