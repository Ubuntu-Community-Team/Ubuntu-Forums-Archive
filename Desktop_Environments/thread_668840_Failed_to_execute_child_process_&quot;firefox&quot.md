---
title: "Failed to execute child process &quot;firefox&quot;"
date: 2008-01-15
forum: Desktop Environments
---

### Post by BSmucks on 2008-01-15
I just started using ubuntu 7.10 yesterday and so far I've had no real problems I couldn't solve myself, with the help of these forums until now.

I was trying to download the steam client from valve and firefox wouldn't download anything, nothing at all, also the google toolbar was completely unusable and at the time there was a firefox window open that I could not close but all the other windows I'd open would. 

I ignored it for a while until I figured that window might be responsable for my downloading problems, so I force quit firefox, that window still remained open so I browsed through all the programs I could terminate and found something called "firefox cache" or something along those lines. So without thinking twice I ignored the warning and terminated it and the window was gone, then i tried opening firefox again I got this error message:

[SIZE="5"]Could not launch application[/SIZE]

Failed to execute child process "firefox" (No such file or directory)

So I restarted ubuntu and tried again and I still got the error, so I installed the firefox that was burned on the install disc so I could see how I could fix it but I've searched around and couldn't find anything on it, or anything that might have been related was so hard to read because the text would cross over itself.

---

### Post by TeaSwigger on 2008-01-15
Honestly I'm confused :p as steam & valves are great for locomotives far as I know, but one quick thing you could try is to see if Firefox's user profile is corrupt.

To do that easily, close all instances of firefox; rename you user profile (that's a hidden folder in your user home folder - those start with a period in the name, to see them in Nautilus, check the option to "show hidden folders") which is probably named .mozilla, to something else; start firefox. Firefox should create a new user profile. If it's working again, you might've installed something wrong or something? You can copy the bookmarks from the old profile into the new one if desired.

---

### Post by nvrmnd on 2008-01-19
you need to right click your firefox icon at the bar and click properties. there should be a command box just paste this /usr/lib/firefox/firefox and that should work

---

### Post by BSmucks on 2008-01-22
Well I tried renaming the .mozilla file in my home folder and i tried changing the command line on the launcher, but still no luck

I can live with this windows version of firefox but it really doesn't work as well as the original one

Edit: Just tried reinstalling version 4.4.5 and that didn't work either, I would try to uninstall it from add/remove programs but....

AHA! I got it, reinstalled it through the Synaptic Package Manager -> World wide web -> Firefox and that worked, thanks for the tips!

---

