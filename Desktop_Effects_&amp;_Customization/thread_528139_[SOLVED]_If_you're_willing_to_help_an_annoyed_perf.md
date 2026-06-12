---
title: "[SOLVED] If you're willing to help an annoyed perfectionist..."
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-17
I'm currently using the Feisty New Human (original, not v2) theme from [http://www.gnome-look.org/content/show.php?content=55365](http://www.gnome-look.org/content/show.php?content=55365) in Feisty.
It's a great theme, but something is troubling me; In the top right corner, there is one little pixel that isn't right. It's outside of the drawn window border line, and it really bugs me for some reason.
What bugs me even more, though, is that I just finished setting up a fresh install of Feisty on my sister's computer and installed this theme to see if the same thing happened, and IT DIDN'T. 
The only thing I find more annoying than things not working is not knowing WHY they won't work.
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-ThemePreferences.png[/IMG]
Does anyone have any idea why *my* theme wouldn't render correctly but *hers* would?


[b]EDIT: 
For anyone else having this problem, I'll post the fix here in the first post.
Thanks to spupy for taking the time to go into the xml and edit it just to fix that one little pixel; Here's his fixed xml file for anyone else who might need it. You need to place it in /home/<your_user_name>/.themes/<name_of_theme>/metacity-1/
Overwrite the old file, you can save it if you want. In theme manager select another theme then select Feisty Human again to load the new files.[/b]

---

### Post by Happy_Man on 2007-08-17
Perhaps you can fix the issue by uninstalling and reinstalling on your computer?

---

### Post by rainwalker on 2007-08-17
I've tried that a few times. I deleted the theme from my .themes directory, along with Glossy Orange (which had this same problem), and reinstalled only this theme.
It still doesn't work.

Thanks for actually reading this, though, I know not many people are going to :)

---

### Post by spupy on 2007-08-17
If you have the knowledge you can dive in the configuration files of the theme. But, as far as i know, the Human theme uses no pixmaps, all is coded, so editing it would be hard. Anyway i imagine it has something to do with a difference in the resolution you and your sister use?

---

### Post by rainwalker on 2007-08-17
I've tried changing resolutions, and it still didn't work.

---

### Post by rainwalker on 2007-08-17
I don't know if it will help, it's more to show that this theme isn't working the way it should;
My separators in Firefox aren't right either. Instead of the solid lines they should be, they're now dashed lines:
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-1-1.png[/IMG]

---

### Post by Mykle87 on 2007-08-17
Could your monitor have a dead pixel?

---

### Post by PhotoJoe on 2007-08-17
If it's just one little spot that's always there, it's probably a 'dead' pixel like mykle87 suggested. Are you using a CRT or LCD monitor? There are actually some fixes out there but I really can't vouch for how effective they are since I've never tried any of them on an actual LCD monitor before.

Try running a video, test screensaver, sample wallpaper, etc. in the full screen mode. If you still see the dot, it's most likely a dead pixel.

I'm not sure the Firefox format problem is even related.......but I'm going to do some homework and see what I can find out.

Good luck and let us know how you make out.

---

### Post by rainwalker on 2007-08-17
Wouldn't a dead pixel just stay in one place? This happens on every window, and it stays there when I move the windows around and stuff.

---

### Post by PhotoJoe on 2007-08-17
Yes, a dead pixel would stay in one place. So, what you're saying is the 'spot' is in one place on every *window* and moves with that window if you slide it around the desktop, rather than staying in one spot on the monitor's screen? Am I correct so far?

---

### Post by rainwalker on 2007-08-17
Exactly.

---

### Post by PhotoJoe on 2007-08-18
Okay...now I think I correctly understand the problem. I'm not sure if that helps or not.:???:
So, you installed your OS, no doubt made changes and modifications to suit you,and *then* installed the new theme. On your sister's computer, you installed the same theme as part of the fresh OS install.....am I right so far?

---

### Post by rainwalker on 2007-08-18
Yeah, I started off on...Dapper, I think?
That's right, Dapper, then upgraded to Edgy and now Feisty.
Hers was just a fresh install of Feisty

---

### Post by PhotoJoe on 2007-08-18
I'm on my Fedora box right now since I haven't finished putting another fan in my Ubuntu machine. Some time this weekend ( I have to work tomorrow) I'll install this theme and see if I can recreate the problem. I upgraded from Edgy to Feisty so maybe I'll have the same problem.

How similar are the settings (windows prefrences, screen resolution, desktop effects, etc.) between your computer and your sister's?

---

### Post by FuturePilot on 2007-08-18
Don't know if this has anything to do with your problem but I just tried that theme out on a fresh install of Feisty and I don't see that pixel.:confused: So perhaps it has something to do with the upgrade? Just thinking out loud. That is very strange.

---

### Post by PhotoJoe on 2007-08-18
That helps a bit. We seem to have verified that the theme in question works fine with a fresh install but is problematic with an upgrade.
I'll be back in a little while....let me see what I can do with Feisty.

---

### Post by rainwalker on 2007-08-18
Alright, thank you both :)

I don't know if it's useful to know, but this theme would only work under Feisty. I originally tried it back on Edgy but it didn't work for some reason. 
I think that's half the reason I'm no obsessed with this; I was all happy that this theme finally worked and then I find that it's not working right.

---

### Post by PhotoJoe on 2007-08-18
You're welcome!

Anyway, my extra case fan is working great but my brain is pretty well cooked. I'll see what I can do tomorrow.  Just so we're on the same page, did you download the Emerald theme or the GTK~Metacity one? There are two downloads on the link you posted and I want to make sure I'm trying to break the same one.

---

### Post by rainwalker on 2007-08-18
I actually have both, but the one I'm talking about is the GTK-Metacity one.

The Emerald one works fine, actually. But I thing that's because I have it set to round the corners or something, I don't know.

---

### Post by PhotoJoe on 2007-08-18
Okay, I'll try the GTk one first and see what happens.

---

### Post by spupy on 2007-08-18
Omg i have that pixel too!! I will try something and report later.

EDIT: I use Debian. I don't have your other problem with the menus, or any other problem, yet. Just that annoying pixel lol
What is  your version of Gnome? Mine is 2.18.3

---

### Post by spupy on 2007-08-18
Ok, I fixed it on my computer, hope the fix works in your computer. The problem got solved when i edited the theme and moved a line with 1 pixel :lolflag:.

In the archive i attached you will find the new XML file for the Metacity theme. You need to place it in /home/<your_user_name>/.themes/<name_of_theme>/metacity/
Overwrite the old file, you can save it if you want. In theme manager select another theme then select Feisty Human again to load the new files.

---

### Post by rainwalker on 2007-08-18
THANK YOU!
You're basically my new hero :)

---

### Post by isaacj87 on 2007-08-18
ahhh damn...someone beat me to it...:)

I was editing the metacity-theme-1.xml file too...

Anywho, that's great that you found a fix!

---

### Post by PhotoJoe on 2007-08-18
Whew! I installed this theme and have spent the last half an hour sliding windows around the desktop without seeing the offending pixel, so I'm back to square one.

Glad to hear you got it fixed!

---

### Post by rainwalker on 2007-08-18
Thank you all for helping, this has bothered me for a while :)

Even the theme's creator wasn't sure what to do

---

### Post by spupy on 2007-08-18
He just didn't make the left and the right top edges symmetrical, missed by one pixel.  :P If you are in touch with him, send him the fix.

EDIT: NP,  i already sent him a message on gnome-look.org

---

### Post by rainwalker on 2007-08-18
Haha, so did I, right after you solved this


Still, I wonder why it worked right on some computers but not ours?

---

### Post by spupy on 2007-08-18
What's your screen resolution? Mine is 1280x800 - widescreen. Only that comes to mind.

---

### Post by PhotoJoe on 2007-08-18
> Still, I wonder why it worked right on some computers but not ours?

I was wondering the same thing. Why is my system, as well as some others, able to render the theme properly when the problem was 'built in' to the package? I used the same download source so I should have seen the pixel. Right?

I feel strangely disappointed that the theme worked for me.:lol:

---

### Post by rainwalker on 2007-08-18
Haha, don't be
I've been going CRAZY trying to figure this out, for at least a month!

---

### Post by PhotoJoe on 2007-08-18
1024x768 on an ancient Trinitron Monitor. It's an old warhorse but *great * for pics and video.

Hmmm....maybe I should up my resolution and then try the theme.

---

