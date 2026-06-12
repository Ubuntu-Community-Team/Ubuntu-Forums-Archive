---
title: "Custom Edgy Usplash"
date: 2006-12-22
forum: Desktop Environments
---

### Post by Steve S. on 2006-12-22
I just upgraded recently to Edgy and reviews are pretty good.  After fixing a couple of things, it looks really good (especially with Beryl ;-)!

Although I do like the new usplash, ever the customizer, I am wondering if there is anyway to change it?

Before you connect me to the standard links ;)  please know that I have been all through the ones that I know about and learned a great deal, but have only been able to get the original picture (with or without scrolling text) or no picture at all and just scrolling text.  Every png I have used (tried both pngtousplash and the tobogl methods) produces no picture and just rolling text, as if the new .so file is not recognizing at all.

Here are the links I've gone through:
[https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

[http://www.ubuntuforums.org/showthread.php?t=82835]("http://www.ubuntuforums.org/showthread.php?t=82835")

I realize that most info out there is for Dapper, and I got it to work regularly with Dapper, but no go with Edgy, even with the modifications that I know about.

Anyone had success with this?  Anyone have any links that I don't know about?

Thanks in advance for your help with this.:D

---

### Post by Steve S. on 2006-12-24
Man...no one?

Perhaps this will give insight.

When I run this:
```
 sudo dpkg-reconfigure linux-image-$(uname -r)
```

I get this:
```
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17.1-10.34 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-25-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Anyone have any idea why I can't get any of these pictures to work?

---

### Post by Steve S. on 2006-12-29
Well, now I have no pictures at all...I can change the size of the scrolling text like a champ (look at the numbers get bigger and smaller!) but no picture.

Man this is frustrating...

---

### Post by Steve S. on 2006-12-29
Bump.

Anyone have any idea how to correct this or know where I can look?  192 views and I'm talking to myself....;)   

Although when i do look around the forums I see that the usplash issue with Edgy is pretty common...

Anyone had any luck with this at all?  I just don't know where to look to figure out why my pictures (selected .so files) aren't showing up.

---

### Post by Steve S. on 2006-12-31
Well, since no one is responding to this but myself, I'll continue to update my progress with the hopes that someone will take what I've done, use it, then be able to create a custom edgy usplash, then they'll tell me what they did!

I got my picture back, and the Ubuntu usplash looks great.  Not custom, but at least I got the intended one back up and running.

1. I had to run this:
```
cd /usr/lib/usplash
```
to get to the usplash directory.

2. Then I ran
```
sudo ln -sf usplash-theme-ubuntu.so usplash-artwork.so
```
to manual establish the bad link from the theme to usplash artwork.

3. I then reran:
```
sudo update-alternatives --config usplash-artwork.so
```
and selected my ubuntu usplash theme to ensure that, using the link that I had manually set before, usplash would use the selection that I wanted out of the alternatives list.

4. I then reran:
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
to get everything configured.

5. I then reran:
```
sudo gedit /boot/grub/menu.lst
```
and looked for the end of boot line for my kernel.  I then changed
```
ro quiet splash
``` to ```
ro vga=791 splash
``` so that I can see everything.  I've found that if I don't do it just this way it doesn't show up on my 1024x768 screen.

Noting that, since I repaired the link manually, it ran, I thought that maybe I could use this info.  Sure enough, I looked in the /usr/lib/usplash directory and saw that I also had Xubuntu and Edubuntu and Kubuntu.  If I followed the steps mentioned above I could change the usplash to each of these.  I can get each of these to run.

But I haven't been able to use this information further.

Here's why:
I find that I can only get the manually repaired links to work if they are for items that are in /usr/lib/usplash and are listed in the alternatives.  And I can't get anything in the alternatives that is already in /usr/lib/usplash.

In other words, I can't manually add (for example) ubuntu-blue.so in /usr/lib/usplash then manually make the link by running step 2 above and then run:
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-blue.so 55
``` (modified from the afformentioned wiki) 'cause it simply will not add this to the alternatives.

Granted, I don't really know what the crap I am doing, just muddling around in the dark.

So, feel free to give comments and assitst.  Anyone?  Anyone?

Also, know how to remove anything from the alternatives list?  I have 13 things on my list, but I can only get 5 of them to work, so I might as well clean up that list.

---

### Post by Steve S. on 2006-12-31
Ok, it doesn't seem to have as much to do with the location as I thought it did.

It instead has to do with the manual adjustment of the link as mentioned above and then making sure you have a good *.so file that is being used.

Right now I am using a "peace" theme [from here]("http://www.mail-archive.com/ubuntu-art@lists.ubuntu.com/msg03303.html") that is actually very nice.  Not custom, but still looks good.

It seems that pngtousplash is not very effective otherwise my custom stuff would have already worked with the suggestions in previous posts.  

I'll stick with what I have for right now, unless anyone is going to give us any tips on customizing our own...

---

### Post by Steve S. on 2007-01-01
I still haven't figured out how to do a custom usplash in edgy, but I have found something that can save you a great deal of freaking time and effort: start up manager.

Using this tool you can set everything simply and easily via a gui settings manager.  I wish I had found this weeks ago.

Look [here.]("http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html")  Then [go here]("http://www.ubuntuforums.org/showthread.php?t=295524") for all the info.

Install is very simple (use the deb file).

Now, once we figure out how to do a custom usplash you can change everything with a simple click of a few buttons.

---

### Post by Steve S. on 2007-01-01
Still not custom, but pretty darn close.

Start up manager let me set this up with minimal effort....

(sorry about the pictures...still don't know how to do screenshots of the boot menu and usplash, so had to photograph...they'll give you an idea of how easily you can customize, though.)

---

### Post by raul_ on 2007-01-01
Have you tried splashy?

---

### Post by Steve S. on 2007-01-01
> **raul_ said:**
> Have you tried splashy?

No, I haven't, 'cause I briefly read something that said it wasn't kept up, but I didn't research too heavily.

Have you used it?  Is it worth looking into for Edgy?

---

### Post by raul_ on 2007-01-01
I don't use it but i think it works fine. This thread is a little old but i think it still works ;)

[http://www.ubuntuforums.org/showthread.php?t=41709]("http://www.ubuntuforums.org/showthread.php?t=41709")

---

### Post by Steve S. on 2007-01-01
> **raul_ said:**
> I don't use it but i think it works fine. This thread is a little old but i think it still works ;)

[http://www.ubuntuforums.org/showthread.php?t=41709]("http://www.ubuntuforums.org/showthread.php?t=41709")

Thanks, raul.  The fact that you are trying to help at all puts you light years above those that haven't responded.

I'm a little leary to use splashy as it seems it is not really an edgy thing.  I'll probably check it out anyway, but I would love to know how it effects edgy.  i had a custom usplahs with dapper with no problems, but haven't been able to pull it off with edgy.  Some consolation is the fact that usplash with edgy is much clearer and higher res.

Anyone used splashy with Edgy?

Either way, thanks for the response...very appreciated.

---

### Post by raul_ on 2007-01-01
from
[http://www.gnome-look.org/content/show.php?content=47351]("http://www.gnome-look.org/content/show.php?content=47351")

> 
Description:
I've only included the 1024x768 version due to file size constraints. There is no included fallback resolution so make sure /etc/usplash.conf matches the resolution of the theme.

To get other resolutions visit

Ubuntu Forum Thread: Usplash - Peace Theme
[http://ubuntuforums.org/showthread.php?t=278301](http://ubuntuforums.org/showthread.php?t=278301)

After installing the deb run

sudo update-alternatives --config usplash-artwork.so

and select the theme. Test the theme to make sure it works for you.

sudo usplash -c

press alt + f7 to get back from the test. If it works for you make sure usplash is configured for the theme

sudo nano -w /etc/usplash.conf

edit the config file to match the resolution offered by the usplash theme. Then install the current theme into your boot image

sudo dpkg-reconfigure linux-image-`uname -r`

It should work :), if not post in the ubuntu forums on the linked thread.


I think it works like that for any theme ;)

and from [http://www.gnome-look.org/content/show.php?content=50468]("http://www.gnome-look.org/content/show.php?content=50468")
> 
INSTALLATION

To install it extract the file in your desktop then from a terminal digit

sudo cp usplash-theme-gray.so /usr/lib/usplash/

then

sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-gray.so 10

and finally

sudo update-alternatives --config usplash-artwork.so

Now update your booting process

sudo update-initramfs -u

That s all


---

### Post by raul_ on 2007-01-01
I actually installed both...but i like the default option better :) just to tell you that it worked for me. I don't know if that's what you wanted

---

### Post by raul_ on 2007-01-01
you should also get a look at this:

[http://www.ubuntuforums.org/showthread.php?t=295524]("http://www.ubuntuforums.org/showthread.php?t=295524")

man, now you got me changing my themes :mrgreen:

---

### Post by Steve S. on 2007-01-02
> **raul_ said:**
> you should also get a look at this:

[http://www.ubuntuforums.org/showthread.php?t=295524]("http://www.ubuntuforums.org/showthread.php?t=295524")

man, now you got me changing my themes :mrgreen:

Adictive, huh?:D 

I've tried all those links, raul, and they work just fine...especially since I've installed Start Up Manager.  That thing rocks.

I haven't used the grey ubuntu one, so I may take a look at it.

But I still haven't been able to create my own and get it to work.  Something about the conversion to an .so file.  I've used the instructions in the wiki and pngtoso (or whatever it is...can't remember this early in the moring) but haven't been able to come up with a good file that works.  THAT is what I need to figure out now.

Yeah, I can change pre-made usplashes now like a champ...

Thanks again for the links, raul.

---

### Post by Steve S. on 2007-01-02
Thanks again, raul_, that gray theme looks pretty cool.

Answer me this: do you have those little pictures, almost like icons, that pop up, starting from left to right, in the upper part of the screen, during boot up?  I get a hard drive, a world, a flower, and a few others as the boot process goes on.

What are those things and is there anyway to not show those?

---

### Post by raul_ on 2007-01-02
Nope...at least i never noticed it...where exactly?

---

### Post by Steve S. on 2007-01-03
> **raul_ said:**
> Nope...at least i never noticed it...where exactly?

Oh, then you must not have the same issue.  Can't miss 'em...across the top of the screen on top of the usplash image....no biggy, just curious.  They don't look bad, just out of place.

---

### Post by Steve S. on 2007-01-03
Figured it out!

Ok, here is what I did, so feel free to copy and then you can customize your own.

Warning: it takes a little work, but the effect is very good.  I'm sure many other will make it look even better (please post your effects for the benefit of others).

Also, as you've noticed throughout this thread, I am just muddling through this, so considering this as a how-to might be premature.  Consider it a suggestion from someone that has been messing with this Edgy usplash thing for a little while.

I used a well known Linux learning strategy: I copied.  I saw in [this thread]("http://www.ubuntuforums.org/showthread.php?t=302104") that Jimmy_r figured out how to do a custom usplash for the Christian Edition of Ubuntu.

So, it should be noted that Jimmy_r has turned out to be the Usplash Ninja, it would seem.  Prop's to him.  He also did the thread about the [Start Up Manager (SUM)]("http://www.ubuntuforums.org/showthread.php?t=295524") that I mentioned above.

He took the original Ubuntu theme from edgy, broke it apart, used gimp and his skills, and made up some new png's for everything, the remade it.

Here is his post:
```
Try this one: usplash-theme-ubuntu-ce.so.tar.gz

Here is how I made it:

Installed package build-essential

Did a
Code:

apt-get source usplash-theme-ubuntu

Extracted the package that was downloaded.

Opened the png files inside with gimp,
cut-resized-pasted the "christian ubuntu" text from your mockup to each png.

Opened the make file in the same directory and did a search-and-replace of "usplash-theme-ubuntu.so" to "usplash-theme-ubuntu-ce.so"

opened a terminal, cd to inside the folder, did a
Code:

make

which created the "usplash-theme-ubuntu-ce.so" file.

Then I installed it with SUM(see signature)

To install it manually:
Code:

sudo cp usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-theme-ubuntu-ce.so sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-artwork.so sudo update-initramfs -u

__________________
```

Prior to doing what he did, I copied the original extracted folder to another location and renamed it, just to be safe.  It should be noted to get that good looking loading bar you have to change all of those png's as well.  Everything has to be color indexed at 256 (not RGB).

Instead of Jimmy_r, to avoid some of the pitfalls that I've encountered, after I had made the *.so file, I did this:

I copied the new *.so file to /usr/lib/usplash:
```
sudo cp /home/usplash-theme-ubuntu-blue.so /usr/lib/usplash/usplash-theme-ubuntu-blue.so
```

And, although SUM might have been able to take care of this, I wanted to be sure, so I manually added the *.so file to the alternatives with this one big long command:
```
 sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu-blue.so 10
```

Then I scrolled through the alternatives and picked it, again manualy although SUM probably could get it done:
```
sudo update-alternatives --config usplash-artwork.so

```

...and picked the usplash-theme-ubuntu-blue.so number.

then ran this to set it up:
```
sudo update-initramfs -u
```

And just for fun I ran SUM (Start up manager) to see if that was the one selected, and of course it was.

Hope that helps.  Glad the mystery has been solved (at least for me).

Oh, here is the png of the usplash I made and the tar of the *.so file (if I attach them correctly) if anyone wants to use them.  [B]I'd attach a screenshot of the usplash, but I don't know how to do that, so someone would have to instruct me.
[/B]
Hope that helps!  Post back if it did, please...

---

### Post by raul_ on 2007-01-03
I'm just glad you figured it out :)

---

### Post by Steve S. on 2007-01-03
> **raul_ said:**
> I'm just glad you figured it out :)

As am I!  Thanks for your help/support!:D

---

### Post by Steve S. on 2007-01-07
Example: **BLUE-ISH USPLASH**

All right, I've been playing and starting to get the hang of it.

Here is a bluish one that I think turned out pretty well.

Use it if you like...if you like it post back.  Enjoy!

(I included a moch-up of what it looks like, without words.  It doesn't look exactly like that, but you get the idea.  I think it looks even better with the text, but that's opinion).

---

### Post by spookykid on 2007-01-20
Hi, you have here valuable information, i'm not a ubuntu user but this howto is great, i'm reading it to try to implement a usplash theme in archlinux and you have saved me from a lot of troubles and frustrations. Thank you. =D>

---

### Post by Steve S. on 2007-01-20
> **spookykid said:**
> Hi, you have here valuable information, i'm not a ubuntu user but this howto is great, i'm reading it to try to implement a usplash theme in archlinux and you have saved me from a lot of troubles and frustrations. Thank you. =D>

Excellent!

---

### Post by jay019 on 2007-03-20
Thanks for the helpful info. I managed to modify my usplash, but it only worked on shutdown. 
Will be trying some of the things from this thread to get it sorted proper.

Cheers!

Jay

---

### Post by djen9999 on 2007-03-20
Same here.  Shutdown is fine but I still get my Kubuntu splash when I first start up.  If you figure anything out, please post.

---

### Post by Steve S. on 2007-03-23
Great!  Glad it was helpful....

I noticed that problem, but worked through it and figured out.  Unfortunately, I can't remember what exactly the step was that fixed that...but it should be somewhere in the thread/how to...

If you figure it out, post back.  I'll check and see if I can find it as well!

---

### Post by EnigMattic on 2007-04-09
> **jay019 said:**
> Thanks for the helpful info. I managed to modify my usplash, but it only worked on shutdown. 
Will be trying some of the things from this thread to get it sorted proper.

Cheers!

Jay

Try

Reinstalling Usplash with Synaptic. :-)

---

### Post by iamajd on 2007-04-17
Wow, thanks for all the useful information....

But, to be honest, I'm hoping I *dont* need to use it.  All I want to do is change the color of the verbose text.  Right now, I use the default Feisty Usplash and, for whatever crazy reason, the verbose text is BLUE.  I would like to make it light grey.  Is there an easier way to do that besides remaking the whole Usplash?

Well, I guess it wouldn't be too bad since I would also like to change the size of the text.

---

### Post by DaveQB on 2007-04-17
Thanks a bunch for this!

I think I have done this before, back when it was way harded and (K)Ubuntu didnt have a boot splash, but had since forgotten (before I created my blog/notes).

This should be what I am after to help make a theme for my company (they are looking to sell Ubuntu systems, have always been a Windows centric shop) so I am excited! :)

Thanks again for your patience and perseverance.

---

### Post by DaveQB on 2007-04-18
> **Steve S. said:**
> Figured it out!

Ok, here is what I did, so feel free to copy and then you can customize your own.

Warning: it takes a little work, but the effect is very good.  I'm sure many other will make it look even better (please post your effects for the benefit of others).

Also, as you've noticed throughout this thread, I am just muddling through this, so considering this as a how-to might be premature.  Consider it a suggestion from someone that has been messing with this Edgy usplash thing for a little while.

I used a well known Linux learning strategy: I copied.  I saw in [this thread]("http://www.ubuntuforums.org/showthread.php?t=302104") that Jimmy_r figured out how to do a custom usplash for the Christian Edition of Ubuntu.

So, it should be noted that Jimmy_r has turned out to be the Usplash Ninja, it would seem.  Prop's to him.  He also did the thread about the [Start Up Manager (SUM)]("http://www.ubuntuforums.org/showthread.php?t=295524") that I mentioned above.

He took the original Ubuntu theme from edgy, broke it apart, used gimp and his skills, and made up some new png's for everything, the remade it.

Here is his post:
```
Try this one: usplash-theme-ubuntu-ce.so.tar.gz

Here is how I made it:

Installed package build-essential

Did a
Code:

apt-get source usplash-theme-ubuntu

Extracted the package that was downloaded.

Opened the png files inside with gimp,
cut-resized-pasted the "christian ubuntu" text from your mockup to each png.

Opened the make file in the same directory and did a search-and-replace of "usplash-theme-ubuntu.so" to "usplash-theme-ubuntu-ce.so"

opened a terminal, cd to inside the folder, did a
Code:

make

which created the "usplash-theme-ubuntu-ce.so" file.

Then I installed it with SUM(see signature)

To install it manually:
Code:

sudo cp usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-theme-ubuntu-ce.so sudo ln -sf /usr/lib/usplash/usplash-theme-ubuntu-ce.so /usr/lib/usplash/usplash-artwork.so sudo update-initramfs -u

__________________
```

Prior to doing what he did, I copied the original extracted folder to another location and renamed it, just to be safe.  It should be noted to get that good looking loading bar you have to change all of those png's as well.  Everything has to be color indexed at 256 (not RGB).

Instead of Jimmy_r, to avoid some of the pitfalls that I've encountered, after I had made the *.so file, I did this:

I copied the new *.so file to /usr/lib/usplash:
```
sudo cp /home/usplash-theme-ubuntu-blue.so /usr/lib/usplash/usplash-theme-ubuntu-blue.so
```

And, although SUM might have been able to take care of this, I wanted to be sure, so I manually added the *.so file to the alternatives with this one big long command:
```
 sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu-blue.so 10
```

Then I scrolled through the alternatives and picked it, again manualy although SUM probably could get it done:
```
sudo update-alternatives --config usplash-artwork.so

```

...and picked the usplash-theme-ubuntu-blue.so number.

then ran this to set it up:
```
sudo update-initramfs -u
```

And just for fun I ran SUM (Start up manager) to see if that was the one selected, and of course it was.

Hope that helps.  Glad the mystery has been solved (at least for me).

Oh, here is the png of the usplash I made and the tar of the *.so file (if I attach them correctly) if anyone wants to use them.  [B]I'd attach a screenshot of the usplash, but I don't know how to do that, so someone would have to instruct me.
[/B]
Hope that helps!  Post back if it did, please...
NB
You need package usplash-dev to get make to work.  Otherwise you will find yourself missing the throbber_back.png.c file.

---

### Post by sblanzio on 2007-04-25
thank you! this post helped me to fix ubuntu usplash!
my posts here:
[http://ubuntuforums.org/showthread.php?p=2530674#post2530674](http://ubuntuforums.org/showthread.php?p=2530674#post2530674)

bye! :)

---

