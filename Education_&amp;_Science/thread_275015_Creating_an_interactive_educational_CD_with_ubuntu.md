---
title: "Creating an interactive educational CD with ubuntu and FOSS"
date: 2006-10-10
forum: Education &amp; Science
---

### Post by vblanton on 2006-10-10
Hello everyone on the ubuntu forums! Thanks for reading my first thread :)  I've used the forums to find help many times, but I've never actually started a new thread here. So, here goes:

I want to create an interactive CD with my :KS k/ubuntu:KS  box using (hopefully) Free Software. The idea is that once the cd pops in to any computer using any reasonably modern operating system, the user can begin learning *something* in an interactive way (It would be nice for it to auto-start, but clicking a file on the cd would be fine as well).  The interactive system will need to sport a navigation menu and tutorials that open up somehow with images, text, audio, video presentation and links to other tutorials on the disc, or a web site.  Lastly, it would be nice to be able to add/remove and update text/audio/video/etc easily so that new versions of the interactive CD, or complete remakes are possible.

I have thought about using Flash (probably with Adobe Director), as I have seen others do, but it would be really awesome if it could be all done with FOSS. I've also thought about an interactive web site, but there are some issues with that such as cross-browser worries (all those people using IE.. yuck!), the fact that it doesn't look professional to have it load in a web browser (especially when it loads in an ugly browser.. ;)), and varying resolutions.

So, anyone have ideas or suggestions? If anything isn't clear, please do ask. I look forward to your replies!

Vlad

---

### Post by rajsarkar on 2006-10-13
hi,

you can use

Istanbul: for capturing screen video
Wink: for capturing screen shots/video etc.

pls do a search in the ubuntu forum - you'll get lot of info ob these two sw. both are FOSS. 

you can use both of them and develop multimedia cd using HTML with applications like Scribus. 

hope it would be useful.

regards, 

raj

---

### Post by jsgotangco on 2006-10-17
I'm currently involved in a project similar to what you have said, and what we did was do everything in xhtml so we could automate the data conversion. To address the cross-browser compatibility, especially for windows, the CD itself already contains portable firefox with a customised userChrome.css so that you'll never need to run the browser in the Windows OS.

Since our videos range from 18-20 minute mpegs, we were able to put at least 4 episodes in one CD-ROM along with the initial text, scripts, selected articles from the wikipedia, then link to external websites.

---

### Post by vblanton on 2009-05-15
Thanks jsgotangco, that answer helped a bunch. I dropped the original project idea, but i'm sure that this'll come up again and i'll work from your idea.

---

