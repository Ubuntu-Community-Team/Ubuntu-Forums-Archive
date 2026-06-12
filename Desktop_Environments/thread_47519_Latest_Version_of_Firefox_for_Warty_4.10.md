---
title: "Latest Version of Firefox for Warty 4.10"
date: 2005-07-08
forum: Desktop Environments
---

### Post by jrc on 2005-07-08
Could someone please clear up my confusion?  My Synaptic Package Manager for my Warty Warthog 4.10 says that my current installed version of Firefox is "0.99+1.0PR .1+revertedto0.9.3-0ubuntu3(warty)."  Synaptic also says that this is the latest version of Firefox.  However, distrowatch.com says that the version of Firefox that is packaged with Warty 4.10 is 0.10.1.  It also says that the version of Firefox with Hoary is 1.0.2 and that the latest version of Firefox is 1.0.4.  Why isn't Synaptic keeping up with the latest version of Firefox?

---

### Post by jrc on 2005-07-12
Well, since I found the answer to my question I might as well post it as a reply to myself so that others who have the same question can benefit.

I found my answer at this website:  [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

If you go to the FAQs section of that website you'll see the following question and answer:

[I]What are Ubuntu Backports?    

Well, let's start with some questions. What version of Gaim is included with Warty? What version of Firefox is included with Warty?
    If you've noticed, it's all pretty old. For the sake of stability, Ubuntu will not update any software with newer version replacements. I question this practice. Fedora and Gentoo are two big-name distros that do provide the latest version of (at least) desktop applications, and they barely ever suffer from stability issues. I want to carry over this practice to Ubuntu, to make it the ultimate distribution.[/I]

So, to get the newer versions of some of your favorite desktop applications you need to go to the repositories offered by the Ubuntu Backports website (backports.ubuntuforums.org).  They have instructions on the website on how to add the site's repositories to your sources list.  The website has repositories for both Warty and Hoary.

I added the Backport repositories for Warty and I now have a more recent version of Firefox that seems to work fine.  Good luck.

---

