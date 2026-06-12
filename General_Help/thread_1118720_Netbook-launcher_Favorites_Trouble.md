---
title: "Netbook-launcher Favorites Trouble"
date: 2009-04-07
forum: General Help
---

### Post by spikedog on 2009-04-07
I am have been running Jaunty on my Lenovo Ideapad s10 and it performs great.  I recently installed the netbook-remix meta package and it works with a couple of "behaviors" that I question.

When running the netbook-launcher, my problem is that the Favorites do not initially display.  If I add to them through the right click, the icons are added to my "other" menu.   After running the menu editor (right click on the menu-panel), the Favorites display.

In troubleshooting this situation, I renamed "other" to "Favorites" and added some icons using the menu editor.   

Initially (after a boot), these do not display.  But running the menu editor and closing it , causes the favorites load/display.  

Is this a bug, or do I just not have things configured correctly?   I have uninstalled Compiz and disabled all desktop effects.  I have also configured to just one desktop.  All packages are up to date with the update manager.

Any thoughts??

---

### Post by relen on 2009-06-12
I had a similar issue with my original AA1 (UNR 9.04) in that the "Favorites" ("Favourites" in my British English setting) menu remained empty. On right-clicking an item in another menu to add it to Favorites I, too, found it added it instead to the "Other" menu, which as a result inadvertently ended up with a strange collection of multiple icons.

I located the file and directory apparently associated with the Favorites menu but they were both owned by root and thus not simply accessed directly.

Significantly, looking in the Main Menu preference setup I noted that "Favorites" (either spelling) did *not* exist in the list of menus, which is rather odd and does not seem to be the case for everyone (I've seen other references to it in these forums where it evidently *does* appear). 

As a result I tried creating a Favorites item in the Main Menu preference applet but I could not get it to display (although this may have been because it had nothing in it, or it might have required a reboot), so I did as suggested above and renamed "Other" to "Favorites" and gave it the heart icon. This worked fine, so I created an alternative "Other" (though goodness knows where the original "Other" icon is - I used something else) and copied the contents back into it by dragging them individually (there seemingly being no other way), deleting them from the new "Favorites". I also deleted the extra icons that had resulted from previous unsuccessful attempts to right-click on apps to create Favorites.

It required a reboot to get menu icon changes to display but everything else showed up immediately.

I now have a useful (rather than an empty) "Favorites" menu and have a pretty easy way of managing its contents. I have not yet had the opportunity to see if right-clicking on an app icon and Adding it to Favorites actually works, however.

---

### Post by croy696 on 2010-04-14
Hey guys,

I had a similar problem and reading these posts really helped me out.

Thansk a lot!

Chris

---

