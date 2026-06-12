---
title: "Which is better with Compiz Fusion: KDE or Gnome"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by What The Deuce on 2007-07-15
I am running Feisty and using Gnome with Compiz Fusion and i love it. I thought i would try my hand with KDE and Compiz Fusion but everytime that I install KDE with "sudo apt-get install kde-desktop" or something like that, i never have much luck.  So now i am stuck at the point that I need to reinstall Ubuntu and I cannot tell if I want to install Ubuntu or Kubuntu.

Really the only KDE app i run is amaroK (and i am wondering if it looks or works better in KDE).  And i used to like KDE because i thought it looked cleaner and more graphical, but that isn't an issue now that I have got CF to work.

One thing i love about gnome is it uses an image from video for the video icon or just a scaled version of the image for picture icons - kde doesn't seem to do that.

I don't know too much about docks (like awn) and which window manager they work best with.  But i had trouble getting awn to work in Gnome.

I love CF in gnome, i guess i am wondering if there are any advantages or disadvantages of using CF in KDE?

Thanks.

---

### Post by acelin on 2007-07-15
Songbird works in anything, and is much better than Amarok. Check it out- no need to run KDE. Plus, most programs that only run in KDE only require minimal parts of it- should not be a problem.

Ty Songbird- blows Amarok out of the water.

---

### Post by Ancheron on 2007-07-15
I agree with you there, acelin. Songbird is extremely nice-It is far better than iTunes, or any thing else I've used.

---

### Post by What The Deuce on 2007-07-15
I appreciate the ideas on songbird, but I am still curious how Gnome compares to KDE with compiz fusion installed.  Are there any noticeable advantages to using one over the other?

EDIT:
Whoa, you weren't kidding about Songbird. I think I found a replacement to amaroK, believe it or not!

---

### Post by qamelian on 2007-07-15
> **What The Deuce said:**
> I appreciate the ideas on songbird, but I am still curious how Gnome compares to KDE with compiz fusion installed.  Are there any noticeable advantages to using one over the other

I've used it in both KDE and Gnome and the only negatives I found were that using Aquamarine instead of Emerald for decorations seemed to make CF somewhat less stable, and some KDE apps that hide in the systray don't like to stay there. Some like the updater and basket used to appear as very tiny windows on the desktop instead of showing up in the systray like they normally would. Other than that, performance and stability seemed about the same as in Gnome.

---

### Post by hyperair on 2007-07-16
You'll also have problem with transparent terminals using Konsole. As far as I know, Konsole only supports pseudo transparency, so it lacks support for compositing. But there's a package called konsole-alpha which is a version of Konsole hacked to support compositing, in Trevino's respoitory. Also, you'll have to install kicker-compiz in KDE because the KDE panel doesn't support Compiz's viewports properly.

All in all, feels hackish to me. And it also performs sluggishly on my computer. ><

---

### Post by dfmalh on 2008-04-10
Hi, I installed Kubuntu desktop (I usually work with Ubuntu/Gnome) to have a look at the KDE environment, and I noticed the following: 

When you use Compiz Fusion under the KDE environment with e.g. 1 desktops, it shows 4 work spaces on the system tray but you only have one desktop. I guess this assists in creating the cube (virtual workspaces), which I actually like. It looks nice and one can spread/group and find applications easy. 

The downside to this setup is that all opened applications is also visible in the bottom bar... thus if you have e.g. your mail, internet browser, a terminal and Open Office running each on a separate workspace, you can always also see them in the bottom bar. This becomes more of a problem if you start opening more and more programs, and all of them are on the bottom bar. The idea of moving an application to another workspace it to have everything less cluttered. This does not happen under Ubuntu/Gnome. Everything is separated.

Then if you create an additional desktop, you end up with 8 workspaces on the bottom bar, and this problem continues with the more desktops you create. If you want 4 desktops, you will end up with 16 workspaces... furthermore, if you have more than one desktop, and you figure out which one of the work spaces belongs to which desktop and you have one application on one desktop, and another (e.g. Desktop 1, workspace1 and Desktop 2, workspace 1)on the other, only one is displayed on the bottom bar...

So the problem must be with the 4 "workspaces" for every desktop.

This problem does not happen in Ubuntu/Gnome.

Any ideas?

---

### Post by hyperair on 2008-04-10
Install the "kicker-compiz" and "kicker-taskbar-compiz' packages. Then exchange your taskbar applet in kicker with the compiz taskbar or something of that sort. Also exchange your pager applet with the kicker compiz pager applet.

---

### Post by dfmalh on 2008-04-15
Hi** hyperair**,

Thanks for your reply. Sorry for the delay on my side, I had to re-install the KDE desktop (I did it via Synaptic Package Manager, I just ticked the kubuntu-desktop and apply).

I installed the "kicker-compiz" and "kicker-taskbar-compiz' packages (also through Synaptic Package Manager).

Then exchange the "Taskbar" applet with  the "Taskbar - Compiz".

I then exchanged my "Desktop Preview & Pager" applet with the "Desktop Preview & Pager - Compiz" applet.

This solved the problem of showing all oped applications on the bottom Taskbar. It now shows only what is open on the workspace you are on. Thanks for the help with that. :)

I still have the problem with multiple desktops, e.g. 2 desktops gives me 8 workspaces, and the first four workspaces shows "Desktop 1" as the common name and workspaces 5-8 shows "Desktop 2" as the common name. So the conflict still exists between the "Workspaces" and "Desktops". You can also not give each workspace its own name... :lolflag:

Any thought on that?

---

### Post by PmDematagoda on 2008-04-15
This thread is rather old and I don't really see the point in resurrecting it, if you want to continue this discussion then you can do so in a new thread of your own.

This thread is closed.

---

