---
title: "Customizing The Appearance of Ubuntu"
date: 2024-07-23
forum: Desktop Environments
---

### Post by springshades on 2024-07-23
I'm dreading this question a bit because either the answer is really simple or there is no real answer. Either way I come across as a bit dumb.

I've finally decided that Kubuntu seems to be nearing the end of its usable path for me, so I'm migrating over to mainline Ubuntu with 24.04. I'm a bit unhappy with the "dark" look as the pure gray is a bit harsh for me. I was looking for a slightly color-tinted dark theme. Maybe I'm just spoiled with KDE having hundreds of theme options that are easy to apply. In Ubuntu, it looks like the options are just Settings > Appearance > Style and then either Default or Dark. The accent color barely does anything. The Gnome Tweaks app doesn't appear to change any of the main interfaces even though I've chosen Yaru-blue where possible.

Are there any additional packages that I can install to provide more than just the two options? When I've searched for tutorials and videos on how to customize the appearance of this release, the options appear to be experimental and dangerous. Most of the examples are like full-blown surgery that will probably end with an unstable desktop environment. Am I missing anything obvious?

---

### Post by currentshaft on 2024-07-24
I've never tried it, but [https://www.gnome-look.org/browse/](https://www.gnome-look.org/browse/) looks relevant to your interests.

---

### Post by ActionParsnip on 2024-07-24
Gnome Tweaks is for Gnome. You are using KDE as you are using Kubuntu, which uses KDE by default, instead of Ubuntu which uses Gnome by default.

---

### Post by oldfred on 2024-07-24
Some examples here:
[https://ubuntuforums.org/showthread.php?t=2351238](https://ubuntuforums.org/showthread.php?t=2351238)
[https://ubuntuforums.org/showthread.php?t=2351238&page=68](https://ubuntuforums.org/showthread.php?t=2351238&page=68)

I still like Kubuntu, so have not used Ubuntu for ages, now.
When I used Ubuntu I used fallback when they converted to Unity, then to Kubuntu.

---

### Post by springshades on 2024-07-24
> **currentshaft said:**
> I've never tried it, but [https://www.gnome-look.org/browse/](https://www.gnome-look.org/browse/) looks relevant to your interests.

This is part of it. This site is actually a sub-site of opendesktop.org which is also where themes are generally uploaded for the KDE environment, so I'm familiar with the site. The difference is just that in KDE, there are tools in the settings menu that list the compatible themes, download them, install them, and apply them for you. My issue has been more along the lines of trying to figure out how to do all of that stuff in Ubuntu/Gnome since I'm not familiar with it.

---

### Post by springshades on 2024-07-24
> **ActionParsnip said:**
> Gnome Tweaks is for Gnome. You are using KDE as you are using Kubuntu, which uses KDE by default, instead of Ubuntu which uses Gnome by default.

Just to clarify in case a brief skim of my original post is ambiguous.

I used to use Kubuntu in the *past*. I know how to do all of this stuff in Kubuntu already.

I've just begun to use Ubuntu now, so I'm asking about how to do this in Ubuntu and Gnome. That's why I tagged the post as [ubuntu] rather than [kubuntu].

---

### Post by springshades on 2024-07-24
> **oldfred said:**
> Some examples here:
[https://ubuntuforums.org/showthread.php?t=2351238](https://ubuntuforums.org/showthread.php?t=2351238)
[https://ubuntuforums.org/showthread.php?t=2351238&page=68](https://ubuntuforums.org/showthread.php?t=2351238&page=68)

I still like Kubuntu, so have not used Ubuntu for ages, now.
When I used Ubuntu I used fallback when they converted to Unity, then to Kubuntu.

Unfortunately, that thread doesn't have a whole lot of *how* to make the customizations. That's fair because it isn't really the point of the thread.

The issue I've been having with Kubuntu for several releases is that it seems like the maintainers are having issues keeping up with even the most basic stuff at this point. I think it has been a slow disintegration since the move away from Unity. Back when the mainline Ubuntu used Unity, it was built heavily on Qt libraries which meant that there was a lot of overlap with KDE users. Back then you could install a small KDE app in mainline Ubuntu without necessarily having to also install hundreds of MB of Qt dependencies.

I just did a clean install of Kubuntu 24.04 because I upgraded the hardware on one of my rigs. I was using 22.04 before the upgrade. On boot, there were no major web browsers in the Discover store. No Firefox. No Chromium. No Opera. None of the proprietary browsers. I don't think it even had Midori.

No big deal, they're probably just all snaps now. Maybe I'm missing some snap dependency? I made sure that snapd, snap-store, and every other snap dependency I could think of was installed. Still nothing in Discover. The snap store itself doesn't load up any packages either. None. Apparently it has some sort of issue refreshing itself.

Discover has always kind of sucked though. Muon always works. Except Kubuntu dropped support for it, and you can no longer install it as of version 24.04.

Synaptic doesn't support snaps.

Some people recommend using Apper for now as a replacement. I'm actually not sure whether it supports snaps as I haven't used it before. With a relatively clean Kubuntu 24.04 install, it has a bug with raising privileges to root. You can't actually install anything from it without running it from the command line, lol. I can do that, but at this point I may as well be running a window manager instead of a DE.


The answer, of course, is that the Kubuntu maintainers aren't incompetent. There just doesn't seem to be enough interest in Kubuntu to provide the resources necessary to keep it maintained.

---

### Post by oldfred on 2024-07-24
When I installed Kubuntu 24.04, it came with Firefox as a snap.
It took a lot of work to totally remove all the snaps as some folders & files were buried pretty deep.
But the standard instructions for converting to Firefox .dep from the ppa worked.
And first thing I install is snaptic, but it now installs snaps in some cases.

---

### Post by springshades on 2024-07-24
Apologies for the quadruple post. It's a bit rude to not answer people who are trying to help me, and this post isn't really directed at any of them. This is my own fiddling around with my problem.

The first sentence of my original post is wrong. This is a fairly typical Linux problem where it is doable but definitely not trivial. The "surgery" that I referred to was the process of getting hyprland to work, but that isn't necessary to change basic theming.

I probably wouldn't have been able to figure out anything without the person/people who put together the "Flat Remix" themes. I really appreciate the fact that they provide installation instructions with all of the different themes that they put out. I haven't tried all of this stuff out yet, so I'm not at the point where I could even attempt something like a walkthrough. Here are some of the steps in case anyone is interested though.

You need to use the "Extensions" app to make sure that you have installed the "User Themes" extension. Then you need to install gnome-tweaks. The Gnome Tweaks app allows you to apply several of the necessary theme types, but it doesn't help you to install them. For the Gnome Shell themes, you need to put the correct folders into your ~/.themes/ folder (which I had to create), and then apply them in the Gnome Tweaks app. For Flat Remix, I had to download a theme package, extract it to a folder, then copy/paste the subfolders out of that main package into my ~/.themes/ folder. The last step took me a minute to figure out because the Gnome Tweaks app doesn't "see" the themes until you've done that. The Gnome Shell modifies the panels on your desktop. You also have to install a GTK 3 theme. That is supposed to follow roughly the same set of steps. It affects the appearance of some of your apps. This can supposedly be applied in the Gnome Tweaks app after you've installed the theme manually by choosing the "Legacy Apps" theme. It sounds like GTK 4 themes need to be copied into a different folder. Since there is no app available to apply them, that needs to be done entirely from command line. Many current themes package GTK 3 and GTK 4 parts together, so you have to break them up manually to put them into the correct folders. GTK 4 themes should handle your main menus and the most up to date apps. The prevalence of GTK 4 *stuff* in Ubuntu 24.04 means that most of the older guides are no longer sufficient to complete the task in the current version.

Unlike KDE, I haven't really found any settings menus or apps to change the appearance of the load up screen (plymouth) or login screen (GDM). But I'm okay with their default appearance, so I honestly didn't look very hard.

---

### Post by springshades on 2024-07-24
> **oldfred said:**
> When I installed Kubuntu 24.04, it came with Firefox as a snap.
It took a lot of work to totally remove all the snaps as some folders & files were buried pretty deep.
But the standard instructions for converting to Firefox .dep from the ppa worked.
And first thing I install is snaptic, but it now installs snaps in some cases.

If you install the "Full" option for Kubuntu, it comes with Firefox as a snap. I may have shot myself in the foot by choosing the stripped-down option during the Kubuntu install, but I certainly didn't expect it to be as completely and utterly broken as it was. And to be clear, I don't mind snaps. I honestly don't care one way or the other. My install literally could not install snaps graphically. I had to do it from the command line either directly with the snap command, by installing transitional .deb packages, or by launching a 3rd party installer from the command line with root privileges.

And to be fair, it isn't truly about that one problem. It's the fact that if they allowed that out of the door on a clean install, I can't trust that distro to be maintained in the future. This isn't the case of a hardware issue or third-party software which would be understandable. This is their own software being completely broken on a clean install even after they've had months to release fixes.

EDIT: Sorry. Made a mistake there. Discover is considered a KDE app. I guess that means that at least in part they can blame some of this on issues with a third party app. All of the issues with snap and the snap store not working are on Kubuntu though.

---

### Post by Dennis N on 2024-07-25
> Many current themes package GTK 3 and GTK 4 parts together, so you have to break them up manually to put them into the correct folders. GTK 4 themes should handle your main menus and the most up to date apps.

No need to break these up. I never do. You can leave the gtk-3.0 and gtk-4.0 folders inside the parent theme folder. 

gtk-3/4 themes you download will not theme Gnome Core Applications (such as Files, Disks, etc) that are using libadwaita to control their appearance. If you want a uniform appearance for all your applications, you must use one of the Adwaita themes for the Legacy applications theme choice.

gnome-shell theme versions should match the gnome-shell version in order to appear as intended. Check before downloading.

"Extensions" is not the best tool to manage gnome-shell extensions, since it will not install them. Use "Gnome Shell Extension Manager" instead.

You can control accent colors when not using a Yaru theme with "Custom Accent Colors" gnome-shell extension.

---

### Post by springshades on 2024-07-25
> **Dennis N said:**
> No need to break these up. I never do. You can leave the gtk-3.0 and gtk-4.0 folders inside the parent theme folder. 

gtk-3/4 themes you download will not theme Gnome Core Applications (such as Files, Disks, etc) that are using libadwaita to control their appearance. If you want a uniform appearance for all your applications, you must use one of the Adwaita themes for the Legacy applications theme choice.

gnome-shell theme versions should match the gnome-shell version in order to appear as intended. Check before downloading.

"Extensions" is not the best tool to manage gnome-shell extensions, since it will not install them. Use "Gnome Shell Extension Manager" instead.

You can control accent colors when not using a Yaru theme with "Custom Accent Colors" gnome-shell extension.

I think that we're probably talking about the same thing with gtk 4. I'm probably just using the wrong words to describe it since I'm only going off of a handful of online sources. The system apps are not considered "legacy apps", so choosing a different gtk theme via the old methods doesn't affect them. The only way to override the appearance of new apps, according to the Flat Remix instructions and a few explanations I've come across online, is an ugly hack to overwrite the appearance of the Adwaita theme itself. You have to copy a chunk of the gtk 3/4 theme's files into the Adwaita themes local settings folder at ~/.config/gtk-4.0 to override the look of gtk 4 apps.

The last little hiccup that I had that wasn't completely clear to me was that you have to then choose the "Default" appearance out of the main settings to make sure the main systems apps are fully using Adwaita. After reading an online explanation of the ugly hack being pulled off, I think I understand the gist of it now. I wasn't originally aware of *why* I was copying a folder full of files into a new place in my local settings as the directions didn't really go into it. I'm going to test this now, but with this hack combined with the "Dark" appearance from Ubuntu's settings, I ended up with Frankenstein apps where parts of the systems apps were using each theme, lol.

The true answer is apparently much closer to my original sentence. Now that I've spent more time digging, the official responses that I've seen is that if you don't like the way anything looks in Gnome, you should switch to a different DE. Major updates to Gnome break most themes. New GTK apps are prone to breaking to the point of being unusable from even minor changes to their appearance. You end up in unstable and unsupported territory pretty much immediately. KDE apparently had to be built from the ground up to be theme-able, and Gnome went with a more "you get what you get" approach. That's fine. It's their choice.

EDIT: Wrong again! Changing between the two different appearance options in Ubuntu's appearance settings did nothing. Frankenstein system apps is the result of all of this. No one should do any of this. Just learn to live with the default look.


Linux is my nemesis.

---

### Post by Dennis N on 2024-07-25
Correct. if you have a gtk.css file in ~/.config/gtk-4.0 then those settings are used instead of the code in libadwaita, which you cannot edit directly. The only thing I change is the accent color by using the "Custom Accent Colors" extension to have a color other than blue. 

I do use a number of Gnome Shell extensions to add to or improve the functionality of the system. The Gnome shell extensions prove to be a very important and attractive feature you don't see in other desktop environments.

Attachment: Appearance > "Styles" on this Ubuntu 24.04.

---

### Post by tea for one on 2024-07-25
If you like the Window Control Buttons similar to the Flat Remix theme, have a look at this css solution.
> This is highly experimental. A set of buttons is drawn over the existing ones. For a purely css solution (Gtk3 & Gtk4 apps only though) see these files:
[https://github.com/icedman/gnome-shell-hammer/tree/master/window-theme](https://github.com/icedman/gnome-shell-hammer/tree/master/window-theme)
In essence, you copy the gtk-3.0 and gtk-4.0 folders and replace the existing folders in /home/username/.config
I use this with the built-in Ubuntu Dark theme and red (device colour profile)
Unfortunately, the snap packages ignore the Window Control Buttons.
Screenshot herewith - Ubuntu 24.04

---

