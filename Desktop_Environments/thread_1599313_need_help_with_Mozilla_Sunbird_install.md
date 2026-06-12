---
title: "need help with Mozilla Sunbird install"
date: 2010-10-17
forum: Desktop Environments
---

### Post by gogolink on 2010-10-17
Hi,

I just upgraded to 10.10 Maverick Meerkat -- actually, did a clean install, with a separate home partition I retained from Lucid -- and thus had to re-install a number of applications.

The one I'm struggling with is Mozilla Sunbird -- which is no longer supported by Mozilla, and not in any repositories I know of.  But I prefer having a separate calendar application to using the Lightning extension in Thunderbird.

I still have the tar-ball (is that what it's called?) of the last Sunbird version Mozilla came out with, sunbird-1.0b1.tar.bz2.  (Can be downloaded at 
[http://www.mozilla.org/projects/calendar/sunbird/l10n_download.html]("http://www.mozilla.org/projects/calendar/sunbird/l10n_download.html").)  I extracted it into a hidden folder (".sunbird") in my home partition, and now have, among many other files, one there that is simply called "sunbird."  It is a shell script, and when executed in terminal, it does open the application -- everything seems to be working, my calendars are still all there, so that's good.

What I don't know is how to run the application in any other way than opening the folder in Nautilus, double-clicking the file, and choosing "Run in Terminal".  I tried to run it using alt+F2. The Run Application-window does know "sunbird", but tells me that it "Could not open location 'file:///home/[my computer's name]/sunbird'"; it says: "Error stating file '/home/[my computer's name]/sunbird': No such file or directory."

I assume that the location given there was the one I used on my Lucid-installation -- unfortunately, I don't remember what exactly I did back then to get Sunbird running...

So I guess my problem is: how to teach my system the terminal command "sunbird", in such a way that it executes the shell script "sunbird" in /home/[my computer's name]/.sunbird.

Can anyone help?

---

