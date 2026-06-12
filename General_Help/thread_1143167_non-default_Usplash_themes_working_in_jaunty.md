---
title: "non-default Usplash themes working in jaunty?"
date: 2009-04-29
forum: General Help
---

### Post by aniruddha on 2009-04-29
Has anyone managed to get any Usplash theme other than the default jaunty theme working? I keep getting a no valid theme for 640x480found error message. And this is after compiling two themes from gnome-look, using a 640x480 image.

---

### Post by bhishan on 2009-04-29
i m using dust theme without any problem

---

### Post by aniruddha on 2009-04-29
Just to clarify- themes such dust etc. work. I was referring to the initial boot usplash themes. I cannot get anything other then the default jaunty one to run. 

Apologies for any confusion caused.

---

### Post by bhishan on 2009-04-29
> **aniruddha said:**
> Just to clarify- themes such dust etc. work. I was referring to the initial boot usplash themes. I cannot get anything other then the default jaunty one to run. 

Apologies for any confusion caused.

Thanks for the info. I will try them and let you know.

---

### Post by Bibek on 2009-04-30
I too have been trying to get themes from gnome-look.org working but have not been able to do it. I was using hardy before and it was working with hardy. What are the changes in jaunty from hardy that makes these old usplash not work ? Also, I use startupmanager to apply the themes.

---

### Post by nandemonai on 2009-04-30
Negative.

I've tried x86 versions, 64bit versions, messing with the /etc/usplash.conf resolution, messing with startup manager resolution all to no avail.

Something is definitely wrong.

Any suggestions?

---

### Post by bdr529 on 2009-04-30
The only working usplash i found is...

[http://www.gnome-look.org/content/show.php/elementaryOS+usplash?content=102110]("http://www.gnome-look.org/content/show.php/elementaryOS+usplash?content=102110")

I don't know why this one works, but you may contact the author.

---

### Post by aniruddha on 2009-04-30
Thanks for the responses people. It does seem as if there is an issue with the usplash in jaunty. I tried both startupmanager and terminal, no change. And the elementaryOS theme posted previously doesn't work for me...

sighs...

---

### Post by Bibek on 2009-04-30
From the usplash posted by bdr529, I have tried the elementaryOS-silver-flat version and it works. I applied it using startupmanager.

---

### Post by nandemonai on 2009-04-30
Is there a difference between 32bit and 64bit usplash themes? I've only seen a couple themes with 64bit variants (which didn't work for me in Jaunty I might add).

---

### Post by aniruddha on 2009-05-01
There is. I had to recompile themes in Intrepid when running 64bit. But they used to work after that. Nothing seems to work in Jaunty.

---

### Post by nandemonai on 2009-05-01
> **aniruddha said:**
> There is. I had to recompile themes in Intrepid when running 64bit. But they used to work after that. Nothing seems to work in Jaunty.

Ah I figured as much. How do you go about recompiling them out of interest?

---

### Post by aniruddha on 2009-05-01
I downloaded the ubuntu-sunrise theme from gnome-look. Edited the image using gimp and and ran sudo make and then sudo make install. There are a couple of others which I tried as well. I am assuming that is 'recompiling' (as I gathered from the Great Google)

---

### Post by theburningor on 2009-05-02
I am in the same situation.  I can only get the elementary OS and the default themes to work, otherwise I just get a text-only boot.  I looks like it tries to change graphics modes between GRUB and the boot sequence and then goes back to text.  I wonder if it is trying to change the graphics mode to something other than what the display can handle?

---

### Post by manpoole on 2009-05-05
im getting the exact same problem as theburningor

---

### Post by aniruddha on 2009-05-09
Hey guys, recompiling some more recent themes worked for me (make sure you are fully updated):

[http://gnome-look.org/content/show.php/Heliocentric+-+Usplash?content=103632](http://gnome-look.org/content/show.php/Heliocentric+-+Usplash?content=103632)

[http://gnome-look.org/content/show.php/Crunchy+Branch-Usplash+Jaunty+%26+Intrepid?content=102489](http://gnome-look.org/content/show.php/Crunchy+Branch-Usplash+Jaunty+%26+Intrepid?content=102489)

I'm going to try with some older themes soon and if anyone is interested, will let you know the results.

---

