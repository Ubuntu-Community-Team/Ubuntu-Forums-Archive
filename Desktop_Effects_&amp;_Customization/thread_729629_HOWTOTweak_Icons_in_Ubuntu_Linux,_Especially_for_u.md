---
title: "HOWTO:Tweak Icons in Ubuntu Linux, Especially for use with Compiz and Avant Window"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by nchase on 2008-03-20
[[IMG]http://bp2.blogger.com/_nCLKbj44niI/R-IMtbghCHI/AAAAAAAAAhY/YCN56BLkQpw/s400/Screenshot-Desktop.png[/IMG]]("http://bp2.blogger.com/_nCLKbj44niI/R-IMtbghCHI/AAAAAAAAAhY/YCN56BLkQpw/s1600-h/Screenshot-Desktop.png")

(Original post and the rest of my blog [here]("http://blog.ahfr.org/2008/03/tweaking-icons-in-ubuntu-linux.html"))

This is the sort of thing where the actual information is spread out across all four corners of the Internet and can rarely be found in one place cohesively. I aim to change that.

Gnome's Appearance Panel does a pretty good job of standardizing icons for a theme you select, but it doesn't get absolutely everything. Those little icons in the top left corner of the window, for instance. Or if you use Compiz or Avant Window Navigator (AWN), many of the icons pulled from the system for usage within those programs. AWN allows you to select custom icons, but those don't always "take" properly. Compiz does not give you this option at all. The result is the ruination of an otherwise seamless experience when you hit alt+tab by way of the wrong icons appearing in the application switcher. Maybe some will be small, and others will be twice as big. Some will be pixelated because they're stretched out; others are crystal clear. The purpose of this guide is to give you a little extra knowledge so that you might create for yourself a more seamless desktop experience. Eye candy certainly isn't everything, but it can make long sessions in front of the computer a lot more pleasant.

This guide should apply to Ubuntu 7.10 (Gutsy) and 8.04 (Hardy). It may work for other distros and other versions of Ubuntu. Alternatively, it may not work for any computer except my own. If that is the case, sorry!

Things you'll want:

    * nautilus-image-converter (apt-get this) -- this is great for resizing images straight from Nautilus without having to open up The GIMP.

    * a nice icon package (I like this one a lot -- David Lanham's artistic style is great at producing a "fun" desktop environment)

    * a dash of paranoia + pack rat mentality so that you'll back up all icons you change -- who knows when you'll need those ugly backups, or what you might need them for...

    * the hard headedness to simply rename a .png file to .xpm and replace lots of xpm files this way -- because I don't know any better and couldn't tell you the difference between png and xpm. My desktop doesn't seem to notice the difference either.


The first step is relatively obvious: go to System > Preferences > Appearance, install your icon package by clicking the install button and locating the package, then select it by customizing the theme and selecting the icon package.

Now that this is taken care of, notice that some icons did not get customized. You'll have to do these yourself.

Common places to find icon files that are used by AWN/Compiz include:

    * Note that the following directories do not allow regular users to modify their contents by default. An easy way to change the file permissions here is to go to a parent directory such as /usr/share/icons (for the next bulleted item below) and running the command 'sudo chmod -R o+w /usr/share/icons/'. This command allows users other than the owner (root) to write to /usr/share/icons/ and all files and folders within that folder because of the recursive flag (-R). 

    * Most programs can be found in '/usr/share/icons/hicolor/48x48'. Icons within the other size-based folders in 'hicolor' may also be of interest to achieve best effects.

    * Firefox icons are different. Perhaps due to it being such a cross platform program, it places them in a different location. You can find them in and around /usr/lib/firefox/icons and /usr/lib/firefox/chrome/default/icons. 

The method you want to follow to replace these icons is to back up the icons that look like the ones you want to replace, then copy/resize/rename the icon you want as the icon you're replacing. It's hacky but you should be able to get it to work.
Note: I have not yet found the location of the OpenOffice pixmap files that would need to be modified to make this seamless for those icons as well.

---

### Post by nchase on 2008-03-21
Anyone know where the matching icons exist for openoffice programs?

---

### Post by misterhead on 2008-03-28
I don't know why the process for installing an icon theme wasn't obvious to me, before, but it makes perfect sense now. Thanx.

---

