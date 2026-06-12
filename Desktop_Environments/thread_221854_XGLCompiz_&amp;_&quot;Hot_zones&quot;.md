---
title: "XGL/Compiz &amp; &quot;Hot zones&quot;"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Jhongy on 2006-07-24
Hello,

I recently installed Compiz and XGL following the instructions on Compiz.net.... I also installed gset-compiz and gcompiz-themer.

I find that I now have four "hot zones"... for wont of the proper terminology. That is, when I point at the top right or bottom left of the screen, all the windows tile for me to switch between them. Similarly, pointing at the top left corner causes a similar animation.

This is cool, but I don't want it - I keep activating the switching/animation by accident. So how do I turn them off?

I have looked through the gset-compiz, and can't find anything that would adjust this functionality (and anyway, gset-compiz doesn't seem to work). I also looked up all the options under Compiz in gconf-editor, and couldn't find it either.

Any advice? I keep pointing at the corners of the screen and losing my window focus... it's exceedingly annoying ](*,) 

P.S.... any idea why gset-compiz doesn't do anything? I set the options in there, but they do nothing. When I close and re-open gset-compiz, the options have reverted to the same way they were before.

TIA

---

### Post by mcduck on 2006-07-24
For now you need to use gconf-editor to configure some features, as gset-compiz is always a little behind of changes made in Compiz..

I'm at work ATM so I can't help with the exact location for those setting, but keep on looking, it's there ;)

---

### Post by dolarsrg on 2006-07-24
Hi!

Try using Gset-Compiz and deactive Scale Plugin. Since I know, that's the plugig what do so, so it must disable the hot zones that you don't like.

Good luck!

---

### Post by dolarsrg on 2006-07-24
Oh! I found something else.

Go to Gset-Compiz and click on "Plugins". Go to the Scale tab and in that configuration panel you will see a zone called "Select Hot Corners".

It must be wath you're looking for.

Usin that (without disabling the plugin as I tell you to do in my other post) you will be able to use the F11 and F12 key to use the feature even if you disable the Hot corners.

---

### Post by jeremytaylor on 2006-07-24
If you want to use gconf-editor to configure/remove these the settings are to be found in 

apps/compiz/plugins/scale/allscreens

just delete the entries for 

initiate_(all/app/whatever)_edge


Jeremy

---

### Post by Jhongy on 2006-07-24
Cool... Thanks everyone. Problem solved.

Since gset-compiz isn't much use, how would I remove it? I installed it through apt-get, so I assume apt-get remove gset-compiz would do the trick?

---

### Post by dolarsrg on 2006-07-24
Yes, you can ;)

But keep in mind that every day there are new versions in the repositories. So, it is going to be more usefull every day :D

Just find it in synaptic and delete it.

Or using apt-get in the same way but with the 'remove' option instead the 'install' one.

---

