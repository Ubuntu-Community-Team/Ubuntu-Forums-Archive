---
title: "Forum fix for Firefox users"
date: 2006-03-15
forum: Forum Feedback &amp; Help
---

### Post by timas on 2006-03-15
**The original post was in the thread about how well we like, or don't like the changes to the forum that have been made, see this link to find it:** [http://ubuntuforums.org/showthread.php?t=144754&page=13#121](http://ubuntuforums.org/showthread.php?t=144754&page=13#121)

This is a fix for Firefox users that contains:
> Full width page;
> Drop-down sub-forms on the main page

And 3 fixes that became appearant right of the bat as other things were changed:
> the page navigation within a multipaged thread is its proper size again
> the dropdown menu's width is fixed
> Quickreply is half the page-size and centered.

Check out this site to find info and to download the FF extension: [http://userstyles.org/stylish](http://userstyles.org/stylish)
**Follow these steps:**
1. Download and install the Stylish extension
2. Restart Firefox (pitty that)
3. Goto ubuntuforums.org
4. Click on the little icon that should be in the right bottom of your statusbar (paper with a pencil)
5. Click 'add style for ubuntuforums.org'
6. Give the new style a name, make sure the enabled box is checked
7. Copy the bellow code into the code area of Stylish and hit save

```

@namespace url(http://www.w3.org/1999/xhtml);


@-moz-document domain(ubuntuforums.org) {
  /* Fixes the page size back to the full width */
  table {width: 100% !important;}

  /* Fixes the size of the pagenav and vbmenu_popup boxes after the above was set */
  div.pagenav table {width: auto !important;}
  div.vbmenu_popup table {width: auto !important;}

  /* Makes quickreply 50% of the total page size */
  #qrform {width: 50% !important; margin: 0 auto !important; display: block !important;}
  #qrform textarea {width: 100% !important;}

  /* Makes the sub-forum in the main-page work as a mouse-over dropdown */
  td.alt1Active div.smallfont {width: 400px !important;}
  td.alt1Active div.smallfont ul {display: none;}
  td.alt1Active div.smallfont:hover ul{display: block;}
  td.smallfont table div.smallfont form {display: block !important;}
}

```

From hereon forward, the page will stretch again, the pagenav table thing is a quick fix to make sure the page navigation doesn't get stretched 100% as well.. the !important tags are required by stylish to instantly apply them while browsing the site.

I'll attempt to fix the subforum hide/unhide thing as well, but not too sure how possible that is going to be..

Disclaimer: I am not trying to battle the mods or the redesign, it's really just because I like it better like this and it gives the other folks who also want it a chance to use it too..

Suggestions, additions, ideas, requests, I'm all for it :)

---

### Post by mcduck on 2006-03-15
As I already said in the original thread, this is great.

I didn't make forums 100% wide, only 96% as it looks better to me. So I added a line with 'body {background: #836849 !important;}' to change that grey background to nice Ubuntu brown :)

edit: it seems that they thought about the same thing.. No need for that fix any more.

---

### Post by bonzodog on 2006-03-15
mcduck: can we see a screenshot of that somewhere? I would like to see that.

---

### Post by mcduck on 2006-03-15
[QUOTE=bonzodog]mcduck: can we see a screenshot of that somewhere? I would like to see that.[/QUOTE]
I attached one to the main thread about forum changes. Here's a link to the image: [http://ubuntuforums.org/attachment.php?attachmentid=7073&d=1142426395]("http://ubuntuforums.org/attachment.php?attachmentid=7073&d=1142426395")

---

### Post by mcduck on 2006-03-15
After some time using this, I decided to leave subforum links as they are. Making them hide/unhide causes thinks to move up and down when moving mouse around the page. It's a bit hard to click a link when it changes it's place when you're moving cursor towards it..

This is what I'm using now:
```

@namespace url(http://www.w3.org/1999/xhtml);

@-moz-document domain("ubuntuforums.org") {

/* Fixes the page size back to the full width */
table {width: 96% !important;}

/* Fixes the size of the pagenav and vbmenu_popup boxes after the above was set */
div.pagenav table {width: auto !important;}
div.vbmenu_popup table {width: auto !important;}

/*Quic Reply area */
#qrform {width: 65% !important; margin: 0 auto !important; display: block !important;}
#qrform textarea {width: 100% !important;}
}

```
Code areas don't use full page yet. But I'll see if I can fix that. :-k

---

### Post by steve.horsley on 2006-03-15
Timas and McDuck: Thanks for showing us a great fix. It will enable me to keep reading the forum - that half-width thing really made me feel claustrophobic. Time I learned something about CSS I guess.

---

### Post by mcduck on 2006-03-15
[QUOTE=steve.horsley]Timas and McDuck: Thanks for showing us a great fix. It will enable me to keep reading the forum - that half-width thing really made me feel claustrophobic. Time I learned something about CSS I guess.[/QUOTE]
All thanks should go to timas. He's the one who first told us about this great extension, and provided the original solution.

I'm not that good with CSS either. And reading through Ubuntuforums source makes my brain hurt.. But I suppose time spent learning more web code is never wasted. :D

edit: now we seem to have some items on the right side. That pretty much ruins my nice full-screen layout :( I guess I'll have to wait and see how these forums end like, and try to fix things then..

---

### Post by timas on 2006-03-15
.. massive redo of the forum, I'ma work on a version where the quicksearch/20 last active threads can be hidden and again full sized forums.. I've got to say though, except for that right sidebar being too busy its a huge improvement :)  Now checking stuff really quick from a fresh Kubuntu install, will get firefox installed in a wee bit... just gota look around to find out wether there's a pre-made package for the 1.5 version

---

### Post by mcduck on 2006-03-16
Now things are looking nice. Sidebar is not there any more when reading the threads, and having it on the front page is OK for me :)

---

### Post by timas on 2006-03-16
I couldn't agree more with you on how its looking now.. I'ma let the sidebar work in for a bit too, see if I can get used to it, the rest all looks superb so my firefox fix is no longer needed :)

---

### Post by mcduck on 2006-03-16
[QUOTE=timas]I couldn't agree more with you on how its looking now.. I'ma let the sidebar work in for a bit too, see if I can get used to it, the rest all looks superb so my firefox fix is no longer needed :)[/QUOTE]
It's actually still very useful with higher screen resolutions :) I hope the sidebar stays on the first page only..

---

### Post by Koybe on 2006-03-17
I removed the subforum dropdown as I do not really like this. Looks messy.
But 100% width is really... really great!

---

