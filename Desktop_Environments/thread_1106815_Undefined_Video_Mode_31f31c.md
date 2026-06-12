---
title: "Undefined Video Mode 31f/31c"
date: 2009-03-26
forum: Desktop Environments
---

### Post by VitaminBB on 2009-03-26
Ive already read several threads on this issue however none of the fixes for others seems to apply to me, im hoping the community can help.

I believe what makes my problem different is the resolution size of my laptop, 1440x900 (widescreen)

When I start my computer and chose Ubuntu from the grub list (im dualing with Windows) I immediately get the "Undefined Video Mode 31f (or 31c depending on which vga=? number I use, 31f=vga799, 31c=vga796).

Now in either vga mode during boot up I get a clear picture but changing the vga=? has no effect on receiving the error.

The startup manager does not have an option for 1440x900 resolution either.

Any ideas how to fix this issue?

---

### Post by VitaminBB on 2009-03-27
Bueller? bueller?

---

### Post by VitaminBB on 2009-03-28
So is this the first time ive stumped the Ubuntu community? or does noone want to bother to help?

---

### Post by VitaminBB on 2009-03-30
If anyone has any idea please help a guy out, its still a problem for me.

---

### Post by mcduck on 2009-03-30
Set it to "vga=ask", and on next boot you'll get a list off all modes available on your computer. Try one that looks suitable, if it's OK then use that in your boot line, if not try some other. 

(you can't just pick the modes from some table on some web site, what modes work for you depend on what your graphics card can handle).

Also note that it's quite possible that there is no mode available for you that would correctly match your display's resolution.

---

### Post by Bobrm2 on 2009-04-07
[http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html](http://gusantov.blogspot.com/2008/05/undefined-video-mode-number.html)

Try this link, works for me.

---

### Post by stevepaul on 2010-04-30
@VitaminBB

I've just had the very same problem which I narrowed down to Startup Manager ...

My screen is 1440x900 same as yours and I had no problems originally ...

Then I suddenly got the same error as you but with a code of 307 ...

If you start up you can get a list of codes that are supported on your machine ...

You need to edit the Grub and change the VGA= ...

I've tried 803 and 854 they both worked OK and I also uninstalled Startup Manager (the cause of my problem - I think)...

Just as an aside if you want to try other codes you need to get yourself a Hex to Decimal converter ...

You'll find this link useful ...

[http://www.easycalculation.com/hex-converter.php](http://www.easycalculation.com/hex-converter.php)

---

