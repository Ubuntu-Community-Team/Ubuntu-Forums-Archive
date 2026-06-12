---
title: "Font Problems Solved for Lucid 10.04"
date: 2010-05-15
forum: Desktop Environments
---

### Post by nodrog1952iii on 2010-05-15
OK.  I have been wrestling with my Ubuntu 10.04 fonts ever since upgraded from Hardy 8.04.  My specific problem was that the fonts presentation for Firefox and Thunderbird both changed with Lucid.  With Hardy, the fonts were virtually identical to Windows with Firefox and Tbird. However, Lucid's fonts are much different and, in my opinion, ugly. I didn't run any intermediate versions of Ubuntu between Hardy and Lucid and so I have no way of knowing if the fonts may have changed earlier than 10.04.  But the bottom line is that I have now figured out how to make the fonts in Lucid appear identical to Hardy and Windows specifically for Firefox and Thunderbird.

Here is how:

1) I installed windows fonts in /usr/share/fonts. In my case, I have the Windows fonts from an old Windows license, however, I would assume that this would work with msttcorefonts but I can't say for sure since I haven't tried it. After installing your Windows fonts then run "sudo fc-cache".

2) This next step is the missing piece.  That is, install the /etc/fonts directory from Hardy 8.04.  I have attached Hardy's /etc/fonts directory to this post. Simply replace your /etc/fonts directory with the attached file (untar the tarball) and then run "sudo dpkg-reconfigure fontconfig". Be sure and save a backup copy of Lucid's /etc/fonts prior to installing the Hardy fonts just in case you decide to revert these changes in the future.

That's it.  Your Firefox and Tbird installations should now present themselves virtually identical to Windows just like Hardy 8.04 did.

This worked for me on a Dell Precision M6300 laptop with an LCD display.

FYI,

Gordon

---

### Post by steve_steve on 2010-05-30
I've been having a similar problem, and what finally fixed it was to go into System > Preferences > System Settings > Appearance (under Look & Feel) > Fonts - and enable anti-aliasing.  

That's what did it for me, anyway.  It was fine before going to Lucid.

---

### Post by ontwowheels on 2010-06-17
> **steve_steve said:**
> I've been having a similar problem, and what finally fixed it was to go into System > Preferences > System Settings > Appearance (under Look & Feel) > Fonts - and enable anti-aliasing.  

That's what did it for me, anyway.  It was fine before going to Lucid.

I looked for this last night, I don't have a System > Preferences > System Settings applet.

---

### Post by Antipodean on 2010-09-24
Thanks very much nodrog1952iii.

I only just recently got around to upgrading from Hardy (mainly because it worked flawlessly for me) and that font problem was really ticking me off.

For me the problem apps were Firefox, Seamonkey and VLC media player.

I am happy to report that your fix/workaround worked perfectly.


[Edit] Just an addition to add something I noticed after applying this.

If "Smooth Scrolling" is enabled in Firefox via Preferences > Advanced > General Tab or in Seamonkey Via "about:config" it plays havoc with some web pages during vertical scrolling.

Disabling "Smooth Scrolling" however seems to fix this problem.

---

