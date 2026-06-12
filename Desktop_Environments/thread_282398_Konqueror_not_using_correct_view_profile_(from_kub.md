---
title: "Konqueror not using correct view profile (from kubuntu-default-settings)"
date: 2006-10-22
forum: Desktop Environments
---

### Post by Soneras on 2006-10-22
This is the most annoying bug that I came ever across in several years of heavy KDE usage - and believe me, there were a lot of bugs.
Anyway I'm telling this because I really try to stay calm and make a well thought out posting, but if I fail, it's because that bug annoys me so much ;)

Info about the installation:
dapper drake
new isntallation
latest kde from kubuntu.org
bug is valid without latest KDE as well (had it before on my previous install)

This is about Konqueror's view profiles. As you may know Kubuntu uses a package called kubuntu-default-settings to install the custom settings the Kubuntu team deemed worth changing. One of those (actually pretty good) changes is a special look for Konqueror. The arrangements of several menubar menus was improved and the shown toolbar icons were minimized. All well and good. Though the previous releases hoary and breezy had a less optimal menu arrangement that was fixed with dapper.

Contrary to the defaults of the previous release the kubuntu-defaults in dapper have (for example) the items "Show Navigationpanel" and "Split View" within the "View" menu. Those were missing previously.
That explaination is just there to make sure the bug is understandable, because those items are a good indication of which view profile you're using.

My problem now is that I'm unable to actually use the improved profile from dapper. In a newly launched KDE session it's usually so that the first one or two file-managing Konqueror windows display the new profile - but every window thereafter has the old profile.
This is so annoying to me becuase the old profile did not only miss the items described before, but it actually displayed the bookmark toolbar in file management mode. That's really putting me off. I can't work when this bookmark toolbar is there - I'm a bit picky probably, but what really bothers me is that I'm unable to get rid of it.
I can remove the toolbar, I can save the view profile. When I do that for ALL previously opened Konqueror windows, then save all newly opened windows will have the bookmark toolbar disabled again. You can tell though that it's still using the old profile by looking at the "View" menu ("Split View" and such are missing). But at least the bookmark toolbar is gone.

Unfortunately this only works until I next log into KDE. So when I start the next session after a reboot this annoying bookmark toolbar is back again there.

After digging through the filesystem for possible places where this profile could be stored and changing it with my own (from ~/.kde...) with a root Konqueror I still can't get rid of it.

I really don't understand why this horrid bug is even affecting me. I did a fresh install and immediately installed all current updates. Though at that time I was of course already logged into KDE, so maybe the erroneous files were already created for my user?!

What I found out is that the file "filemanagement" is located in thise directories:

/home/chris/.kde/share/apps/konqueror/profiles
/usr/share/apps/konqueror/profiles/filemanagement
/usr/share/kubuntu-default-settings/kde-profile/default/share/apps/konqueror/profiles/

Still all fiddling around with those files was in vain. Any ideas and recommendations are welcome. Additionally I'd be interested if this only affects me or if others can reproduce it. After all I couldn't find any results about this via a quick and frustrated forum search.](*,) 

Sorry for the long text - still hope someone bothers to read and reply =)

---

