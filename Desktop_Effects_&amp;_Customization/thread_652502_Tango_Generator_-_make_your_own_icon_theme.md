---
title: "Tango Generator - make your own icon theme"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by mejy on 2007-12-28
I'm pleased to announce the third iteration of my Tango Generator application.  While it's still very much in its infancy, I hope it will be useful to anyone looking for a customised or more complete icon theme for their Gnome or XFCE desktop.  It enables users to create their own icon theme from more than 20 component theme and a variety of configuration options, creating a personalised and unique look, as well as allowing users to share their themes in the form of configuration files.

If anyone's interested, you can check out the [ official site]("http://mejogid.ohallwebservices.com/site/index.php?q=node/1") - with configuration files, a FAQ, poles, a discussion forum and much more -  or its [gnome-look page]("http://gnome-look.org/content/show.php/Tango+Generator+3?content=72361"), which contains some answers to common questions in the comments and allows you to vote for the application.

I've put a good deal of time into making it the best I can, and if anyone would like to help with any aspect of it, or needs help using it, please post here or on the official website.  I'm also more than happy to answer any questions you may have.

Thanks for your time,

mejogid/mejy

---

### Post by empthollow on 2007-12-28
i've never heard of your program before but what a great idea.  Thanks for posting here.

---

### Post by mejy on 2007-12-31
Thanks for the kind words.  I've now updated it to include debian packages for all Ubuntu versions since 6.06, and have improved support for older versions, where it's most needed.  

If anyone has any suggestions at all, I'm happy to act on them and am still looking for any python coders willing to help with my frivolous hobby.

---

### Post by kpkeerthi on 2008-01-11
So I installed tango-generator and it created a bunch of tar.gz files ~/.tango-generator. Which ones should I choose? Some are as small as few KBs which are apparently missing a lot of icons causing gnome to default to stock icons when installed. I checked the home page. Can't find even the basic instruction as to how to use this. Anyone able to figure out how to 'use' this. Thanks.

---

### Post by FuturePilot on 2008-01-11
You shouldn't have to install anything. It does it for you. Just go System>Preferences>Appearance and click Customize. Then go to the Icons tab and you should see the new one that it just generated.

By the way, I love this tool. It gave me an awesome set of Tango style icons. Even my icon for Exaile is Tangofied. :D

---

### Post by kpkeerthi on 2008-01-12
Thanks... that gave me some start. But where is the documentation, getting started or read me file?<gasp> Nevermind.

---

### Post by mejy on 2008-01-27
Right, sorry about the lack of documentation.  I've been going on the assumption that it's fairly self explanatory, and as the feature set and GUI is still very much in flux I'm not yet prepared to maintain a README given my current time constraints.  If anyone else has the time to make a start on some more detailed documentation, I'd be more than willing to include it.

---

### Post by empthollow on 2008-01-28
i have a question.  I created a theme that i like pretty well with your program :) thanks: but there is a theme that i would like to include icons from and it does not show in your gui.  It is the leopard icon themes from the mac4lin project.  the theme works fine if i chooose it but i would like to combine it with other themes as your program seems to automagically do.  Could you help me to get the theme to show in your program or at least explain why it won't.  Thanks in advance.

---

### Post by mejy on 2008-01-29
> **empthollow said:**
> i have a question.  I created a theme that i like pretty well with your program :) thanks: but there is a theme that i would like to include icons from and it does not show in your gui.  It is the leopard icon themes from the mac4lin project.  the theme works fine if i chooose it but i would like to combine it with other themes as your program seems to automagically do.  Could you help me to get the theme to show in your program or at least explain why it won't.  Thanks in advance.

There are a couple of reasons why it won't work.  First off, the Tango Generator will only work correctly with themes that supply icons in all sizes specified by the Tango Style Guidlines - 16x16, 22x22, (ideally 32x32) and scalable.  This is generally only the case with Tango or Tangoesque themes.

If you use a theme that doesn't apply all these sizes they generally rely on Gnome scaling a different size because it can't find the one it's looking for - if that size is supplied by another theme, you'll get extremely inconsistent icons.  I may in the future include a way to provide custom themes but that's a pretty significant effort (much of which is just adding dirty hacks to get things to work).

I have to admit I'm not a big fan of the OS X/Vista imitation icon themes, and they don't go particularly well with Tango themes as a whole so it's not top of my priorities right now.

It may be possible to hack this into working by copying the Mac4Lin theme over a Tango theme.  However, where the Mac4Lin one is missing certain sizes Tango will still override and you'll probably get a very inconsistent look.

Edit:  On further inspection, the Mac4Lin theme is already using a few incompatible hacks such as pngs in the "scalable" directory (which should only contain svgs) and contains many very incomplete sizes.  Essentially, unless either their theme or the generator is significantly modified you won't have much luck.  Sorry about that.

---

### Post by empthollow on 2008-01-29
i looked at that theme and thought that it was odd that there were pngs in the scalable directory.  I don't know much about icon sets, i thoughs if you replace icons with a differnt pic of the same name.  This method does work if your icons are the right size but is very time consuming.  I managed to create a theme i liked much better with your program anyway.  thanks for the response.

---

### Post by GamingMazter on 2008-01-29
Awsome. Sounds really good. I hadn't heard of your program before though :)

---

### Post by mejy on 2008-01-29
> **empthollow said:**
> i looked at that theme and thought that it was odd that there were pngs in the scalable directory.  I don't know much about icon sets, i thoughs if you replace icons with a differnt pic of the same name.  This method does work if your icons are the right size but is very time consuming.  I managed to create a theme i liked much better with your program anyway.  thanks for the response.

Glad you understand (there's a real lack of logic in the packaging of many themes out there at the moment, and it's quite annoying from the point of view of the generator).  If you've come up with a good configuration, you may be interested in sharing it on the discussion forums I've set up.

> **GamingMazter said:**
> Awsome. Sounds really good. I hadn't heard of your program before though :)

Cheers, hope you enjoy using it.

---

### Post by Ferdil on 2008-03-30
As I said on the other topic, your site is down.

---

### Post by kpkeerthi on 2008-03-31
@mejy,
I see some of the toolbar icons in gtkpod not using tangofied ones (when using the tango config file). Is it possible to have all the toolbar icons consistent?

---

### Post by mejy on 2008-04-08
> **Ferdil said:**
> As I said on the other topic, your site is down.
Should be back up now.
> **kpkeerthi said:**
> @mejy,
I see some of the toolbar icons in gtkpod not using tangofied ones (when using the tango config file). Is it possible to have all the toolbar icons consistent?
It's possible, but will be part of the next significant update if at all.  Esentially, gtkpod and numerous other apps use their own prepackage icons rather than inheriting from the GTK icon theme, making it very difficult to skin them - essentially, each one has to be individually replaced and given the variety between distributions this can range from bring complicated to impossible.

---

