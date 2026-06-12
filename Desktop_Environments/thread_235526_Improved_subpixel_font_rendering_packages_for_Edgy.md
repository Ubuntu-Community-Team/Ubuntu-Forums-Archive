---
title: "Improved subpixel font rendering packages for Edgy"
date: 2006-08-13
forum: Desktop Environments
---

### Post by hugmenot on 2006-08-13
Earlier this year FreeType developer David Turner posted some patches for Cairo and Xft that improved the rendering of fonts on LCD screens (but also CRTs with Trinitron layout). These were put up with the proviso that he was unsure whether they would infringe patented algorithms around Microsoft&#8217;s ClearType technology.

The most recent patches by David have been incorporated into a series of packages that replace the libraries libreetype6, libcairo2 and libxft2 on Edgy. The patches move the filtering from Xft and Cairo to Freetype with the effect that letters have less color fringing and more faithful letter outlines. This is achieved by more advanced subpixel filtering methods and getting rid of stem quantization. Some people dislike this kind of &#8220;hack&#8221; visually, but for many it is a good trade-off of letter contrast and font aesthetics. These patches have meanwhile been released with FreeType 2.3.0.

User **mlind** is hosting readymade packages for Edgy in his own repo. These are the sources (enter in /etc/apt/sources.list)

```
deb http://www.telemail.fi/mlind/ubuntu edgy fonts
deb-src http://www.telemail.fi/mlind/ubuntu edgy fonts
```

The signing keys for mlind&#8217;s repo can be obtained with these commands
```
gpg --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -
```

Then update your package cache (apt-get update) and start an upgrade (apt-get dist-upgrade or equivalent). The patched packages will be installed over the official unpatched versions since they have a slightly higher version number. To get back to the standard packages use the &#8220;Package &#8594; Force version...&#8221; function in Synaptic on all packages listed under &#8220;Origin &#8594; elisanet.fi&#8221; or an equivalent function with other tools.

It&#8217;s up to taste (or debate) whether the font internal shape instructions (hints) lead to better results or the automatic hinter that uses generic heuristics. The two systems &#8211; i.e., either the byte-code interpreter or the auto-hinter &#8211; can be toggled with 

```
sudo dpkg-reconfigure fontconfig-config
```

Be sure to set subpixel rendering to &#8220;always&#8221; on the second screen (and bitmap fonts to &#8220;No&#8221;). The amount of hinting applied can be adjusted in the Gnome Font Settings dialog.

To reduce the superbold appearance it might help to switch the autohinter off for bold faces.
This can be done by adding some lines in the .fonts.conf file in the user home directory or in the system-wide /etc/fonts/fonts.conf. A complete user file is attached to this post. 
```
<match target="font">
 <test name="weight" compare="more"><const>medium</const></test>
 <edit mode="assign" name="autohint"><bool>false</bool></edit>
</match>
```

The patches alone can be found on [David&#8217;s Freetype page]("http://david.freetype.org/lcd")
and in a FreeType release > 2.3.0 where the code has to be enabled with the macro FT_CONFIG_OPTION_SUBPIXEL_RENDERING before compiling.

---

### Post by mlind on 2006-08-17
I'll subscribe to this thread. Although I'm not Edgy user yet, I'm going to install these packages once Knot 2 is out.

---

### Post by desperado666 on 2006-08-17
And i need the original turner patches to build new ones.

Does somebody have them?

---

### Post by mlind on 2006-08-17
> **desperado666 said:**
> And i need the original turner patches to build new ones.

Does somebody have them?

Those aren't the two patches mentioned on first post? You can download source package(s) from repository mentioned on first post too, and get patches from debian/patches folder.

I can rebuild and upload the packages if required.

---

### Post by no1wantdthisname on 2006-08-17
I prefer the default font rendering.  These packages make fonts really blurry.

---

### Post by MetalMusicAddict on 2006-08-17
> **hugmenot said:**
> These were put up with the proviso that he was unsure whether they would infringe patented algorithms around Microsoft&#8217;s ClearType technology.
So why would he think they would. Wouldnt you know one way or another? Honest question.

---

### Post by Amaranth on 2006-08-17
It's best not to check. You get in more trouble for knowingly infringing on a patent.

---

### Post by hugmenot on 2006-08-17
> **no1wantdthisname said:**
> I prefer the default font rendering.  These packages make fonts really blurry.

After using the udated patches for a couple of days I really wonder whether you&#8217;re right. I can&#8217;t help the impression that contrast was better with Davids Turner&#8217;s original patches.
Jinghua told me that they were a direct port however. Could be the newer Freetype, though.

---

### Post by Amaranth on 2006-08-17
I turned off all hinting, it looks a lot like OS X or WinXP fonts now.

---

### Post by saracen on 2006-08-22
> **hugmenot said:**
> After using the udated patches for a couple of days I really wonder whether you’re right. I can’t help the impression that contrast was better with Davids Turner’s original patches.
Jinghua told me that they were a direct port however. Could be the newer Freetype, though.
Ya I agree.  They definitely feel more blurry.  What font are you using there in your screenie?  And what gtk and compiz themes?

---

### Post by hugmenot on 2006-08-22
> **saracen said:**
> Ya I agree.  They definitely feel more blurry.  What font are you using there in your screenie?  And what gtk and compiz themes?

I&#8217;m going to ask Jinghua for a screenshot of his desktop.
My settings are more or less vanilla Gnome/Compiz.
The screenshot depicts Opera, however, with a Clearlooks-derived skin that I made.

Here&#8217;s another shot with my GTK application font being Corbel. And it quite definitely is more blurry than before.
[http://bugzilla.gnome.org/attachment.cgi?id=71310&action=view](http://bugzilla.gnome.org/attachment.cgi?id=71310&action=view)

---

### Post by mlind on 2006-08-22
@hugmenot,

You've probably tried this with "no stem snapping on LCD mode" patched **freetype** package, like it was with Dapper? Does it make any difference?

---

### Post by eewald on 2006-08-22
if these pictures are any indicator - breezy has it better.

---

### Post by hugmenot on 2006-08-22
> **mlind said:**
> @hugmenot,

You've probably tried this with "no stem snapping on LCD mode" patched **freetype** package, like it was with Dapper? Does it make any difference?

Yes I did; I posted my comparison in the OP. However I again switched back and forth between original/patched freetype and see no difference whatsoever *for GTK windows* (cf. the attached difference screenshot).
My only explanation is that Opera uses Xft for rendering fonts while GTK conversely only uses Cairo.

I made a comparison by simulating some GTK-rendered strings on my screen inside of Opera and in my eyes it&#8217;s clearly better. I attached a GIMP format image with layers. If you toggle the Opera layers on and off you&#8217;ll see that Opera has better contrast, while GTK is grayish. I suspected that the Clearlooks gtkrc uses gray fonts, but no, it specifies black as text color.


[HTML] 44   text[NORMAL]      = "#000000" # black
 45   text[PRELIGHT]    = "#000000" # black
 46   text[ACTIVE]      = "#ffffff" # white
 47   text[SELECTED]    = "#ffffff" # white
 48   text[INSENSITIVE] = "#b5b3ac" # dark beige[/HTML]

---

### Post by hugmenot on 2006-08-26
Another sample of text that caught my eye today.
Kind of convices me that inside of my browser font rendering is alright. (slanted stems have some problems but the rest is impeccable IMO.)
This is the[ source page for comparison]("http://www.kaourantin.net/2006/08/pthreads-and-signals.html") (needs Candara to match however).
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=14923&d=1156640358[/IMG]

---

### Post by mlind on 2006-08-28
I uploaded new libcairo2 to repository (and bumped libxft2 just in case..).
Makes any difference with newer version?

---

### Post by hugmenot on 2006-08-28
> **mlind said:**
> I uploaded new libcairo2 to repository (and bumped libxft2 just in case..).
Makes any difference with newer version?

Thanks for tracking the update, mlind.
I made a new screenshot and there&#8217;s no change.
However reading the libcairo2 changelog.gz there has been some explanation by Behdad concerning subpixel rendering configuration in fonts.conf files. I wonder whether we have to adapt to that. (It didn&#8217;t grok it :-|  )

---

### Post by malte on 2006-09-08
```
Impossibile ottenere http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/binary-amd64/Packages.gz  404 Not Found

```
Is the repo offline?

P.S.: notice I'm using amd64...

---

### Post by mlind on 2006-09-08
> **malte said:**
> ```
Impossibile ottenere http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/binary-amd64/Packages.gz  404 Not Found

```
Is the repo offline?

P.S.: notice I'm using amd64...

Sorry, no binaries for amd64 packages :( You can download the source packages and compile them if you wish.

Can I somehow compile amd64 specific packages with current deb build-tools without manually setting up a cross-compile environment?

---

### Post by hugmenot on 2006-09-24
David Turner today posted details about the intellectual property MS holds and about th1e future of LCD rendering in FreeType:
[http://permalink.gmane.org/gmane.comp.fonts.freetype.user/1912](http://permalink.gmane.org/gmane.comp.fonts.freetype.user/1912)

my comment: Patents suck.

---

### Post by Neo40 on 2006-09-28
Hi

I have just did a fresh install of latest Edgy and then I applied the patch to improve fonts. Yeah, it works great for me, but now the firefox menu font's are too big (maybe 14 or 16). All others applications are fine. How can I fix this problem?

Thanks

---

### Post by reacocard on 2006-09-28
> **Neo40 said:**
> I have just did a fresh install of latest Edgy and then I applied the patch to improve fonts. Yeah, it works great for me, but now the firefox menu font's are too big (maybe 14 or 16). All others applications are fine. How can I fix this problem?


Open Firefox's preferences, and under the 'Content' section there's a spot to change your font size.

---

### Post by Neo40 on 2006-09-29
> **reacocard said:**
> Open Firefox's preferences, and under the 'Content' section there's a spot to change your font size.

I'm talking about the menu like File, Edit, Bookmarks, etc...So, even if I change the font size, the menu wont change.

---

### Post by mlind on 2006-09-29
> **hugmenot said:**
> David Turner today posted details about the intellectual property MS holds and about th1e future of LCD rendering in FreeType:
[http://permalink.gmane.org/gmane.comp.fonts.freetype.user/1912](http://permalink.gmane.org/gmane.comp.fonts.freetype.user/1912)

my comment: Patents suck.

Damn that's sad news.. :(
Hopefully these patches get maintained by someone(s) though..

---

### Post by hugmenot on 2006-09-30
Yes, /he/ will, see here:

[http://lists.nongnu.org/archive/html/freetype/2006-09/msg00069.html](http://lists.nongnu.org/archive/html/freetype/2006-09/msg00069.html)
[http://lists.nongnu.org/archive/html/freetype-devel/2006-09/msg00043.html](http://lists.nongnu.org/archive/html/freetype-devel/2006-09/msg00043.html)
[http://lists.nongnu.org/archive/html/freetype/2006-09/msg00080.html](http://lists.nongnu.org/archive/html/freetype/2006-09/msg00080.html)
[http://lists.nongnu.org/archive/html/freetype/2006-09/msg00078.html](http://lists.nongnu.org/archive/html/freetype/2006-09/msg00078.html)

The deal is he is working on putting the subpixel rendering stuff completely into Freetype, i.e., including filtering. Xft and Cairo will need to be patched to disable their filtering code. All this will depend on the config macro FT_CONFIG_OPTION_SUBPIXEL_RENDERING being enabled at compile time which he advises all distros to stay away from, lest they want to be infringing on the several patents he cited.
Which means more work for us :) and it seems there wont be fancy font stuff in any distro in the future unless something interesting happens. All that means people have to actively search for it and get improved fonts by partisan methods.

---

### Post by hugmenot on 2006-09-30
There appeared a Cairo 1.0.4 patch 2.2 h ago here:
[http://david.freetype.org/lcd/](http://david.freetype.org/lcd/)

We&#8217;ll just have to wait for the 1.2.4 patch and can get started. We&#8217;ll need to upgrade to FreeType CVS, enable FT_CONFIG_OPTION_SUBPIXEL_RENDERING and replace the old patches to Xft and Cairo with the new ones. That should be it.

---

### Post by mlind on 2006-09-30
Interesting :)
I'll check this out later today, thanks for the update.

---

### Post by Neo40 on 2006-09-30
> **hugmenot said:**
> There appeared a Cairo 1.0.4 patch 2.2 h ago here:
[http://david.freetype.org/lcd/](http://david.freetype.org/lcd/)

We’ll just have to wait for the 1.2.4 patch and can get started. We’ll need to upgrade to FreeType CVS, enable FT_CONFIG_OPTION_SUBPIXEL_RENDERING and replace the old patches to Xft and Cairo with the new ones. That should be it.

I have downloaded the two files but I don't know how to apply the patch...?

---

### Post by hugmenot on 2006-09-30
First of all, the Cairo patch is for the version that is in Dapper, i.e., 1.0.4.
That&#8217;s why I said we&#8217;re waiting for 1.2.4. 
If you want to try it out you&#8217;ll have to get the sources of the affected packages, apply the patch, and rebuild plus install the result.
I really don&#8217;t have enough time to walk you through all of that right now [-( .

---

### Post by SlCKB0Y on 2006-10-01
WOW!

This has solved my biggest complaint about ubuntu. I always thought distros like SuSE had much nicer looking fonts. 

They now look as good in ubuntu.

---

### Post by ruffneck on 2006-10-04
The patches works wonderfully!

mlind, did you sign the packages in the repos? If so, can you post the key?

Thanks.

---

### Post by mlind on 2006-10-05
> **ruffneck said:**
> The patches works wonderfully!

mlind, did you sign the packages in the repos? If so, can you post the key?

Thanks.

Yes, packages are signed. I think this should work
```

gpg --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

```

---

### Post by shining on 2006-10-05
What about making a poll for seeing if people find that subpixel font rendering better or worse with this patch ?

Because I personally find it worse. I tried using it for one day.. it was hard.

---

### Post by mlind on 2006-10-05
> **shining said:**
> What about making a poll for seeing if people find that subpixel font rendering better or worse with this patch ?

Because I personally find it worse. I tried using it for one day.. it was hard.

Sure, go ahead. Results were very impressive with Dapper, but I'm not currently using this with Edgy myself. I'm eagerly waiting David Turner to release patches against newer libcairo2 and libxft2 (and freetype?) though..

---

### Post by ruffneck on 2006-10-06
> **mlind said:**
> Yes, packages are signed. I think this should work
```

gpg --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

```

Works a charm... thx much!

---

### Post by NoTiG on 2006-10-06
does anyone know if 64 bit packages will be available?

---

### Post by brainkilla on 2006-10-07
Since there are some who complained about blurriness of fonts in Edgy being more patent, I have to say the following procedure proved effective in my case and improved the font rendering and kerning even in comparison to Dapper:

1. Install the packages from the repo mentioned at the beginning of this thread
2. sudo dpkg-reconfigure fontconfig
3. In contrast to Dapper, in gnome-font-properties do select subpixel smoothing, full hinting and RGB subpixel order. Kill X, log in again and enjoy. 

 This is by no means guaranteed outcome for the rest of Edgy users, but worked 100% in my case.

---

### Post by shining on 2006-10-07
Using the unofficial packages **adds** blurriness to fonts when you are using subpixel with full hinting.
If you are not using subpixel, it has no effect at all.

---

### Post by reacocard on 2006-10-07
For edgy, the following produces the best results for me.

after installing the packages, do a
```
sudo dpkg-reconfigure fontconfig-config
```
select "native","automatic" and "no", in that order.
do a
```
sudo dpkg-reconfigure fontconfig
```
open System-> Administration-> Font, select "subpixel smoothing", then go to "details".
Select "Subpixel", "Full", and "RGB", in that order.
Restart X and enjoy the improved fonts.

---

### Post by forcotton on 2006-10-07
Seems to me fonts in Gtk is not as dark as in Firefox or in Qt. IMHO this lack of contrast makes it look fuzzier. I've install the packages (cairo and xft) in the repository. Maybe there is something wrong with cairo? (Which only Gtk uses)

---

### Post by Rob2687 on 2006-10-07
IMO fonts look great Edgy without any extra stuff.

I have Smoothing set to Grayscale and Hinting set to Slight.

---

### Post by forcotton on 2006-10-08
> **Rob2687 said:**
> IMO fonts look great Edgy without any extra stuff.

I have Smoothing set to Grayscale and Hinting set to Slight.

I thought the same, but one day I got curious and installed the patch. Guess what? It's even better. There is still room of improvement.

---

### Post by EisenPM on 2006-10-10
the authentication doesn't work for me...

it says something about the key server is not known [in german...]

---

### Post by mlind on 2006-10-10
> **EisenPM said:**
> the authentication doesn't work for me...

it says something about the key server is not known [in german...]

If it's a fatal error instead of warning, import public part of the signing key using instructions on post [#32]("http://www.ubuntuforums.org/showpost.php?p=1583896&postcount=32").

---

### Post by EisenPM on 2006-10-10
I am sorry, I mean that the importing of the public key did not work. 

now I tried again, and all is well. probably the server was down when I tried the first time.

thanks for this thread, my gnome looks beautiful now!

---

### Post by c4r1 on 2006-10-10
there was a ubuntu libcairo update some minutes ago. the patched packages need a update.

---

### Post by mlind on 2006-10-10
> **c4r1 said:**
> there was a ubuntu libcairo update some minutes ago. the patched packages need a update.

too late, already updated ;)

---

### Post by c4r1 on 2006-10-10
:-) you are very very fast.
thx a lot

---

### Post by mercurysquad on 2006-10-10
whew... for a moment i was pulling my hair over the craptastic fonts that had come back after the ubuntu update. Why the hell can't Ubuntu incorporate these patches already?!!

---

### Post by hugmenot on 2006-10-10
Once Ubuntu is really is rich and famous the patent holder will come after them. That&#8217;s why.

And big props to mlind for being continuously on the ball.

---

### Post by mercurysquad on 2006-10-10
> **hugmenot said:**
> Once Ubuntu is really is rich and famous the patent holder will come after them. That’s why.

And big props to mlind for being continuously on the ball.

I see...
And yes big THANK YOU to mlind!

---

### Post by ruffneck on 2006-10-10
BIG UP mlind!

---

### Post by grendelkhan on 2006-10-10
Has anyone noticed Cairo gtk themes losing their Animation recently??  Maybe I messed something up, but it seems like after a reboot one day, WHAM no animated progress bars.

This is affecting both Murrina and Clearlook-Cairo themes.

---

### Post by ruffneck on 2006-10-11
hmm.. I have noticed that my cursor busy animation has changed after the latest round of updates...dunno..something is a bit weird.

---

### Post by mlind on 2006-10-11
> **grendelkhan said:**
> Has anyone noticed Cairo gtk themes losing their Animation recently??  Maybe I messed something up, but it seems like after a reboot one day, WHAM no animated progress bars.

This is affecting both Murrina and Clearlook-Cairo themes.

Does this happen with official libcairo2 too?

btw. thanks actually go to hugmenot, I'm just packaging this stuff by following provided instructions :mrgreen:

---

### Post by grendelkhan on 2006-10-11
> **mlind said:**
> Does this happen with official libcairo2 too?

Not a clue, I haven't run the official Cairo packages since yours came out.  This just happened really recently.  At first I thought it was something I did, so I recompiled Murrine and there was no change.

I do remember the animation was enabled right off the bat with the default Cairo packages, and that didn't change after I installed yours.

I'm stumped.

---

### Post by hugmenot on 2006-10-11
What I would like to know is why the keyboard layout doesn&#8217;t render anymore (the one that can be reached by right-clicking the keyboard-indicator applet).
And David is again increasing the tension unduly, methinks. I want to have that 5-tap wide filter on my own screen.

---

### Post by brainiac on 2006-10-14
> **mlind said:**
> Does this happen with official libcairo2 too? 

yes it does.. i recently noticed it too with the default libcairo2 and the murrine themes

---

### Post by GazaM on 2006-10-14
> **brainiac said:**
> yes it does.. i recently noticed it too with the default libcairo2 and the murrine themes

Animations being disabled in themes by default lately has nothing to do with cairo packages.

It depends completely on the theme you use. The Clearlooks and Murrine engines both support animations, but in the default themes these are not enabled. If you want to enable them, simply edit the gtkrc file of whichever theme you're using.

To do this, simply open up the themes gtkrc file in gedit (or your text editor of choice) and go to the appropriate section... The best way to explain is really just to show the actual text:

snippet from MurrinaAqualsh theme:
```
engine "murrine"
{
scrollbar_color     = "#93c1ff"
contrast            = 1.0
menubarstyle        = 2 # 0 = flat, 1 = glass, 2 = gradient
menubaritemstyle    = 1 # 0 = menuitem look, 1 = button look
listviewheaderstyle = 0 # 0 = flat, 1 = glass
squaredstyle        = 0 # 0 = default (rounded), 1 = squared
animation           = FALSE
}
```

Change to:
```
engine "murrine"
{
scrollbar_color     = "#93c1ff"
contrast            = 1.0
menubarstyle        = 2 # 0 = flat, 1 = glass, 2 = gradient
menubaritemstyle    = 1 # 0 = menuitem look, 1 = button look
listviewheaderstyle = 0 # 0 = flat, 1 = glass
squaredstyle        = 0 # 0 = default (rounded), 1 = squared
animation           = TRUE
}
```

---

### Post by grendelkhan on 2006-10-15
The themes I use do have it enabled - the themes never changed, only the animation.

Since this happened in both Clearlooks and Murrine, my assumption was it was linked to Cairo.  And someone else noticed, so I'm not going insane.

---

### Post by chiklit on 2006-10-16
Is there a way to install libcairo2-dev with the patch installed? I need it to fulfill dependencies for other packages but it won't install because the patch is 1.2.4-1ubuntu2.1 and it's 1.2.4-1ubuntu2.

---

### Post by mlind on 2006-10-16
> **chiklit said:**
> Is there a way to install libcairo2-dev with the patch installed? I need it to fulfill dependencies for other packages but it won't install because the patch is 1.2.4-1ubuntu2.1 and it's 1.2.4-1ubuntu2.

Yes, repository contains libcairo2-dev too. You need to use matching -dev package for library, in this case you want libcairo2-dev (1.2.4-1ubuntu2.1).

---

### Post by chiklit on 2006-10-16
> **mlind said:**
> Yes, repository contains libcairo2-dev too. You need to use matching -dev package for library, in this case you want libcairo2-dev (1.2.4-1ubuntu2.1).

Ah, didn't notice it wasn't in my sources file anymore. Thanks. :)

---

### Post by sha_man on 2006-10-27
is there no way to get this for amd64?

---

### Post by Pausanias on 2006-10-27
Thanks for the info, hugmenot. And thanks for fielding the questions on my thread during my absence. Thanks to mlind for the repository.

I've updated the head post on the original thread ([this one](http://ubuntuforums.org/showthread.php?p=1041769)) to point here.

And now for my question. Regarding your old modifications to libfreetype:

[http://ubuntuforums.org/showthread.php?p=1336712&highlight=freetype#post1336712](http://ubuntuforums.org/showthread.php?p=1336712&highlight=freetype#post1336712)

Do you feel like adding a package to the repository with these modifications as well? Or shall we hand-apply the patch via your cryptic instructions :p ?

---

### Post by hugmenot on 2006-10-27
I don&#8217;t see what you need. If you run Edgy you don&#8217;t need to modify FreeType. The patched packages for Cairo and Xft are enough. For dapper the packages are all in your thread.

I am actually running an even newer patch by David Turner himself now (the one I mentioned earlier). With it the fancy filtering is moved to be done inside of FreeType completely. The problem is that I haven&#8217;t yet figured out whether I did something wrong or whether the new patches in combination with FreeType CVS actually made things worse.

The result speaks for itself:
first image = old rendering
second image = new rendering

---

### Post by Pausanias on 2006-10-27
Well, here's the reason. With the latest patches from mlind's repository, I actually like the way "slight" hinting renders the normal text. The problem is, it also superbolds the bold text. "Full" hinting doesn't superbold, but I don't like the results on normal text as much.

I seemed to remember that your freetype patches made a difference for this particularly narrow situation, but now I'm not sure... any hints?

The attached example shows the full hinting, no superbolding (top) and the slight hinting with superbolding (bottom) for the same area of the screen.

---

### Post by isolationism on 2006-10-28
Just adding my voice to the (small, so far) chorus hoping that binary support for AMD64 might not be too far behind. Normally I wouldn't shy away from just rolling my own, but I'm not comfortable enough with Ubuntu's paradigm to know how to manage self-compiled and installed vs. managed packages.

It also looks as though there's some confusion as to whether this is in fact an improvement or not; for me, my fonts in Edgy appear identical to what they looked like in Dapper (for better and for worse; most serif fonts, especially Georgia, still look awful and some even verge on illegibility). Maybe it's best to wait for the dust to settle on the "best approach" before worrying about compiling binaries for those of us who appear to be in the minority, here.

My personal thanks go out to those who are working on this unofficial project; It will almost certainly never become an official addition to any Ubuntu package repository, but font rendering in Ubuntu (and Linux in general) is a massive issue that affects what almost every desktop Linux user does for most of the time they are at the computer. 

Please know that your efforts are greatly appreciated.

---

### Post by chaosgeisterchen on 2006-10-28
> **hugmenot said:**
> I don&#8217;t see what you need. If you run Edgy you don&#8217;t need to modify FreeType. The patched packages for Cairo and Xft are enough. For dapper the packages are all in your thread.

I am actually running an even newer patch by David Turner himself now (the one I mentioned earlier). With it the fancy filtering is moved to be done inside of FreeType completely. The problem is that I haven&#8217;t yet figured out whether I did something wrong or whether the new patches in combination with FreeType CVS actually made things worse.

The result speaks for itself:
first image = old rendering
second image = new rendering

Which font are you using?

---

### Post by hugmenot on 2006-10-28
That&#8217;s Candara as specified by the CSS of that page.

---

### Post by kpprem@gmail.com on 2006-10-28
Members,

I used the old packages for font rendering for ubuntu 6.06 and it worked fine. Could you please list the steps for ubuntu 6.10. 

Thanks,
Prem

---

### Post by chaosgeisterchen on 2006-10-28
Question:

How come that Qt-Apps have poorer smoothing than GTK ones? I run Konqueror and GAIM here and GAIM has much smoother fonts.

What do I have to enable/disable concerning fonts to get the same results?

---

### Post by reacocard on 2006-10-28
> **kpprem@gmail.com said:**
> Members,

I used the old packages for font rendering for ubuntu 6.06 and it worked fine. Could you please list the steps for ubuntu 6.10. 

Thanks,
Prem

Add these lines to your sources.list
```
deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts
```

Then do
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by silhouette on 2006-10-28
The repository doesn't seem to be existent anymore...

**Edit**: No wait, it's there. Never mind...

---

### Post by benjaminzsj on 2006-10-29
Thanks for the patch. What's left for me is the shadow below/above the curve of the character, especially greater size than 10.

---

### Post by freewind on 2006-10-29
Hello All.
Sorry for my english.
I install the patch. But i don't understand, how import the public key for this repository. Should you put the instruction for newbie.

Thank you.

---

### Post by hugmenot on 2006-10-29
> **freewind said:**
> Hello All.
Sorry for my english.
I install the patch. But i don't understand, how import the public key for this repository. Should you put the instruction for newbie.

Thank you.

I updated the first post with more details.

---

### Post by Janux on 2006-10-29
Works great, thanks :)
But I have a problem with japanese fonts, they don't display very well. Odd since I used the Dapper patches and they looked good

Any idea?

---

### Post by hugmenot on 2006-10-29
I guess for really reading Japanese this is better.
There are just too many contingencies in Japanese script for the Autohinter to work well. That&#8217;s why FreeType enbles the ByteCode Interpreter for Japanese. I think.

---

### Post by hugmenot on 2006-10-29
> **chaosgeisterchen said:**
> Question:

How come that Qt-Apps have poorer smoothing than GTK ones? I run Konqueror and GAIM here and GAIM has much smoother fonts.

Qt uses Xft, GTK instead uses Cairo.
> 
What do I have to enable/disable concerning fonts to get the same results?[QUOTE]
Are they really poorer. For me Xft was a lot better than Cairo.
Screenshots?

---

### Post by hugmenot on 2006-10-29
> **chaosgeisterchen said:**
> Question:

How come that Qt-Apps have poorer smoothing than GTK ones? I run Konqueror and GAIM here and GAIM has much smoother fonts.

Qt uses Xft, GTK instead uses Cairo.
> 
What do I have to enable/disable concerning fonts to get the same results?
Are they really poorer. For me Xft was a lot better than Cairo.
Screenshots?

---

### Post by zgornel on 2006-10-30
Huge improvement in font quality. :D

---

### Post by msmeyer on 2006-10-31
Note that I do NOT have sub-pixel rendering enabled (I don't think it looks better on my LCD). However, using those libraries fixed Firefox the appearance of Firefox for me! Firefox now looks like Gnome apps (or Thunderbird, for that matter) again, though previously, Firefox would look much more blurry, but Gnome apps would look the same as before. Why that is is beyond me, any pointers appreciated.

---

### Post by mlind on 2006-10-31
@ hugmenot

What's your take about new font packages uploaded to experimental repository?
I probably screwed up/missed something with freetype2 CVS build..

---

### Post by mlind on 2006-10-31
for amd64 folks, if someone provides the binaries for me, I'll try to put those in the repository too.

---

### Post by hugmenot on 2006-10-31
> **mlind said:**
> @ hugmenot

What's your take about new font packages uploaded to experimental repository?
I probably screwed up/missed something with freetype2 CVS build..
Well, I need some more opinions on the results. Someone with an educated eye should tell me whether it looks better or worse than before by scrutinizing the images in this post. In my eyes there are more color artifacts
[http://www.ubuntuforums.org/showpost.php?p=1673893&postcount=66](http://www.ubuntuforums.org/showpost.php?p=1673893&postcount=66)

Your experimental packages exactly match the results I reported in that post.

EDIT: The pictures linked above contain an Xft sample. Attached is a Cairo sample. On top is the old appearance on the bottom the new patches.

---

### Post by mlind on 2006-10-31
There were few Debian/Ubuntu patches that needed to dropped to get the CVS build to compile. I should check if dropped/applied patches are actually relevant or not. This might affect quality too.

IMO there's some colored artifacts that probably shouldn't be there. This is probably freetype2 thingy, libcairo2 and xft2 were just rebuild from earlier version.

Any ideas if enabling full bytecode interpreter instead of just the "non-patented portions" affects quality somehow?

---

### Post by Imrahil on 2006-11-01
```
freetype (2.2.1-2) unstable; urgency=low

  * Enable full bytecode interpreter instead of just the
    "non-patented portions".
  * Use $(CURDIR) instead of $(PWD) to build with sudo. Closes: #367579.

 -- Keith Packard <keithp@keithp.com>  Wed, 17 May 2006 00:00:35 -0500

```

Full, patented bytecode interpreter has been enabled since May. This probably won't be causing issues here.

---

### Post by gryan on 2006-11-01
> **mlind said:**
> for amd64 folks, if someone provides the binaries for me, I'll try to put those in the repository too.

I'm running AMD64 and I'd be happy to provide some 64-bit packages if you all will help me with the process. I noticed in the first post the package versions are:

libcairo2=1.2.4-1ubuntu1.1
libxft2=2.1.10-1ubuntu1.2

however when I check my Synaptic for Edgy, it shows me:

libcairo2 = 1.2.4-1ubuntu2.1
libxft2 = 2.1.10-2ubuntu1.2

So you can see that the libcairo version number is a different. Is this a typo?

---

### Post by hugmenot on 2006-11-02
No, I forgot to update that part.
I will just drop it.

---

### Post by gryan on 2006-11-02
> **hugmenot said:**
> No, I forgot to update that part.
I will just drop it.

Okay, then.

I've downloaded the respective source packages from the [www.elisanet.fi](www.elisanet.fi) repository and built them using "dpkg-buildpackage -rfakeroot -b" I now have the following packages:

libxft2_2.1.10-1ubuntu1.2_amd64.deb
libxft2-dbg_2.1.10-1ubuntu1.2_amd64.deb
libxft2-dev_2.1.10-1ubuntu1.2_amd64.deb

libcairo2_1.2.4-1ubuntu2.1_amd64.deb
libcairo2-dbg_1.2.4-1ubuntu2.1_amd64.deb
libcairo2-dev_1.2.4-1ubuntu2.1_amd64.deb

How do I get these to mlind for him to put in the repository?

Thanks!
George

---

### Post by RiGLEY on 2006-11-03
Hi! 

Can You help me? I have installed these updated fonts, but I want to go back to the Edgy defaults. How can I do it? Thanks!

---

### Post by hugmenot on 2006-11-03
```

sudo aptitude install libcairo2=1.2.4-1ubuntu2 libxft2=2.1.10-1ubuntu1

```

And disable the repo.

How I found out? Use apt-cache:
```
 apt-cache madison libcairo2 libxft2 libfreetype6
```

---

### Post by hugmenot on 2006-11-03
Some progress. I enabled the BCI with dpkg-reconfigure and cleared all my fonts.conf customizations. Now some fun results.
With hinting set to slight appearance is good. I must still be using the Autohinter at slight. I think they force it at that setting. At medium and strong fonts start to look funky. Playing around with my application font I found one that I am happy with (even it being a serif font).

left: slight; right: medium

Attached

---

### Post by RiGLEY on 2006-11-03
Thanks hugmenot!
I get some color-artifacts with the default, but it seems more crisp, than the patched one.

---

### Post by mlind on 2006-11-03
@ hugmenot

I finally had the time to apply David Turner's libXft-2.1.7-lcd-filter patch against libxft 2.1.10. Does this patch improve font quality over earlier (experimental) libxft version or should patch be reverted?

You should reinstall libfreetype6, libxft2 and libcairo2 from the repository (I forgot to bump the libcairo version, so use aptitude reinstall).

I *think* there are less artifacts now, and fonts look bit smoother.

```

libfreetype6=2.2.1+cvs20061103-0ubuntu1 
libcairo2=1.2.4-1ubuntu2.2
libxft2=2.1.10-1ubuntu1.3

```

---

### Post by dredoz on 2006-11-04
Hi mlind,

I would like to install your new packages but it seems that the libfreetype6=2.2.1+cvs20061103-0ubuntu1 you're mentioning is not available from your repository, is it supposed to be there or elsewhere?

Thanks for the great work!

---

### Post by hugmenot on 2006-11-04
> **dredoz said:**
> Hi mlind,

I would like to install your new packages but it seems that the libfreetype6=2.2.1+cvs20061103-0ubuntu1 you're mentioning is not available from your repository, is it supposed to be there or elsewhere?

Thanks for the great work!

Take this line:
```
deb http://www.elisanet.fi/mlind/ubuntu edgy experimental
```

---

### Post by dredoz on 2006-11-04
Thanks!

Everything looks perfect now with these packages!

---

### Post by mlind on 2006-11-04
> **dredoz said:**
> Thanks!

Everything looks perfect now with these packages!

Thanks for the feedback. Do you think results are better with **experimental** packages than with packages in **fonts** repository?

If so, I should probably make experimental packages as default.

---

### Post by gryan on 2006-11-04
> **hugmenot said:**
> Take this line:
```
deb http://www.elisanet.fi/mlind/ubuntu edgy experimental
```

I was able to get the source package for freetype from the experimental repository, but when I attempt to get the source for cairo, it conks out with the following message:

$ apt-get source libcairo2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2905kB of source archives.
Get:1 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (dsc) [896B]
Get:2 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (tar) [2883kB]
Get:3 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (diff) [21.7kB]                                             
Fetched 2883kB in 1m55s (25.0kB/s)                                                                                                   
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.dsc](http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.dsc)  MD5Sum mismatch
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.diff.gz](http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.diff.gz)  MD5Sum mismatch
E: Failed to fetch some archives.

The fact that I'm running AMD64 shouldn't make a difference, but I mention it in case I'm wrong. :-)

- George

---

### Post by mlind on 2006-11-04
I probably forgot to upload updated checksums. Should be okay now.

---

### Post by bbolzano on 2006-11-04
Thanks mlind! I'm using experimental packages and the fonts look great :) Is there any way to apply these patches to OpenOffice too?

Bernard

---

### Post by gryan on 2006-11-04
> **mlind said:**
> I probably forgot to upload updated checksums. Should be okay now.

Thanks! The freetype package builds fine, but the cairo package from the experimental repo fails with:

/home/gryan/fonts/experimental/cairo/libcairo-1.2.4/src/cairo-ft-font.c:56:10: error: #include expects "FILENAME" or <FILENAME>

---

### Post by mlind on 2006-11-05
> **gryan said:**
> Thanks! The freetype package builds fine, but the cairo package from the experimental repo fails with:

/home/gryan/fonts/experimental/cairo/libcairo-1.2.4/src/cairo-ft-font.c:56:10: error: #include expects "FILENAME" or <FILENAME>

Make sure you have the correct (CVS version) libfreetype6-dev package installed, so you're actually building against newer freetype.
If this doesn't work, try replacing debian/patches/cairo-1.2.4-lcd-filter-1.patch with attached one.

---

### Post by dredoz on 2006-11-05
> **mlind said:**
> Thanks for the feedback. Do you think results are better with **experimental** packages than with packages in **fonts** repository?

If so, I should probably make experimental packages as default.

Hi mlind,

Thanks to you for the packages!

That's only my opinion but on my edgy setup "experimental" look way better than "fonts", for example I can now see perfect fonts on this blog [1] while with the "fonts" packages there were many artifacts.

[1] [http://blog.ianbicking.org/](http://blog.ianbicking.org/)

---

### Post by mlind on 2006-11-05
> **dredoz said:**
> Hi mlind,

Thanks to you for the packages!

That's only my opinion but on my edgy setup "experimental" look way better than "fonts", for example I can now see perfect fonts on this blog [1] while with the "fonts" packages there were many artifacts.

[1] [http://blog.ianbicking.org/](http://blog.ianbicking.org/)

IMO fonts look way better now too, so I made "experimental" packages as default in fonts repository.

---

### Post by Janux on 2006-11-05
> **hugmenot said:**
> I guess for really reading Japanese this is better.
There are just too many contingencies in Japanese script for the Autohinter to work well. That&#8217;s why FreeType enbles the ByteCode Interpreter for Japanese. I think.
The Japanese fonts use bitmapped fonts by default. In my opinion, they looks bad, so I forced them to use autohinter too and I think they look great now!

If anyone wants to try, add this in your /etc/fonts/local.conf file to disable embedded bitmaped fonts.
```

        <match target="font">
                <edit name="embeddedbitmap" mode="assign">
                        <bool>false</bool>
                </edit>
       </match>

```

If do you want this to apply only on Japanese fonts, use this instead:
```

        <match target="font">
                <test name="lang" compare="contains">
                        <string>ja</string>
                </string>
                <edit name="embeddedbitmap" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>

```

---

### Post by mlind on 2006-11-05
> **bbolzano said:**
> Thanks mlind! I'm using experimental packages and the fonts look great :) Is there any way to apply these patches to OpenOffice too?

Bernard

I'm pretty sure it's possible, OpenOffice uses freetype for font rendering.

I was looking through [http://www.openoffice.org/FAQs/fontguide.html](http://www.openoffice.org/FAQs/fontguide.html) for
explanation why fonts look so ugly on OO now. Any ideas?

---

### Post by hugmenot on 2006-11-05
I would be interested to see some screenshots. Best would be screenshots before and after uprgading the packages.

---

### Post by VFiend on 2006-11-05
Thanks a lot for this, mlind. I compiled the packages for amd64 and they've been working out really nicely for me. I'm just about to compile the new version that you just put in there, and I'd be happy to upload the debs after so more people can enjoy them without having to compile anything.

---

### Post by VFiend on 2006-11-05
Actually, it doesn't seem to compile, unlike the previous version...

```
../../src/xftglyphs.c:28:4: error: #error "FreeType 2.2.2 or later required to compile this version of libXft"
../../src/xftglyphs.c:32:10: error: #include expects "FILENAME" or <FILENAME>
../../src/xftglyphs.c: In function 'XftFontLoadGlyphs':
../../src/xftglyphs.c:418: warning: implicit declaration of function 'FT_Library_SetLcdFilter'
../../src/xftglyphs.c:418: warning: nested extern declaration of 'FT_Library_SetLcdFilter'
../../src/xftglyphs.c:418: error: 'FT_LCD_FILTER_DEFAULT' undeclared (first use in this function)
../../src/xftglyphs.c:418: error: (Each undeclared identifier is reported only once
../../src/xftglyphs.c:418: error: for each function it appears in.)
../../src/xftglyphs.c:540: error: 'FT_LCD_FILTER_NONE' undeclared (first use in this function)
make[3]: *** [xftglyphs.lo] Error 1
make[3]: Leaving directory `~/tmpfonts/xft-2.1.10/obj-x86_64-linux-gnu/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `~/tmpfonts/xft-2.1.10/obj-x86_64-linux-gnu'
make[1]: *** [all] Error 2
make[1]: Leaving directory `~/tmpfonts/xft-2.1.10/obj-x86_64-linux-gnu'
make: *** [build-stamp] Error 2
Build command 'cd xft-2.1.10 && dpkg-buildpackage -b -uc' failed.
E: Child process failed
```

---

### Post by mlind on 2006-11-06
@ VFiend

You'll need to compile the freetype package first, and then install libfreetype6-dev (2.2.1+cvs20061103-0ubuntu1) before compiling cairo and xft.

Could you compile packages using pbuilder/sbuild? Thanks for your efforts on this.

---

### Post by VFiend on 2006-11-06
> **mlind said:**
> @ VFiend

You'll need to compile the freetype package first, and then install libfreetype6-dev (2.2.1+cvs20061103-0ubuntu1) before compiling cairo and xft.
Ah, thanks

> **mlind said:**
> Could you compile packages using pbuilder/sbuild? Thanks for your efforts on this.
I suppose I could try. Never used it before in my life but I see there's a link in your sig so I'll check that out

---

### Post by neo_reloaded on 2006-11-06
Screenshot after applying patches from elisanet attached.
I never got satisfied with the smoothing from

```

deb http://www.elisanet.fi/mlind/ubuntu edgy fonts
deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

```

so I have rolled back to edgy's default packages. 
My screenshot is having "Corbel" font, but looks bad

At the same time, I admit that "hugmenot"'s screenshots are excellent. That is what I had in my Dapper installation with "turner's patches"

---

### Post by VFiend on 2006-11-06
> **mlind said:**
> Could you compile packages using pbuilder/sbuild? Thanks for your efforts on this.

And we're done. Just put the results folder in a tar.gz and threw it up on a random free hosting service.

[http://senduit.com/6aae23](http://senduit.com/6aae23)

Let me know if there's anything else you'd like, and thanks again for the service you're doing

---

### Post by msmeyer on 2006-11-06
For your info:

On Dapper:

* Firefox looks fine
* Thunderbird looks fine
* OpenOffice looks fine

With the original (edgy) packages:

* Firefox looks smeary
* Thunderbird looks fine
* OpenOffice looks smeary

(see [http://www.mesw.de/support/firefox_thunderbird.png](http://www.mesw.de/support/firefox_thunderbird.png))

With the original elisanet.fi font packages:

* Firefox looks fine
* Thundbird looks fine
* OpenOffice looks smeary


Now after (automatically) upgrading freetype packages to revision 2.2.1+cvs20061103-0ubuntu1:

* Firefox looks smeary (again)
* Thunderbird looks fine (as always)
* OpenOffice looks smeary (as always on Edgy)

Note that I still won't get it why Thunderbird looks fine and other apps don't. Thunderbird, Firefox and OpenOffice all link dynamically to /usr/lib/libfreetype.so.6 (you can see this using ldd). If anyone knows the answer to this, I'd really be grateful to hear it. I think trying to answer this would make much more sense than trying to create new packages which alternatingly look fine for 50% users and don't for the other 50%.

Also, note that I DO NOT USE subpixel smoothing. I have always been using grey-scale smoothing.


Markus

---

### Post by benjaminzsj on 2006-11-06
Thanks, after the patch, everything looks perfect in Deja Vu.
Are those packages optimized only for FreeType?

---

### Post by hugmenot on 2006-11-06
> **neo_reloaded said:**
> 
At the same time, I admit that "hugmenot"'s screenshots are excellent. That is what I had in my Dapper installation with "turner's patches"

Yes but only with certain font settings (I favor the Luxi series currently). The small "d" in your image is what I get also.
These kinds of problems are hinting problems.

---

### Post by mlind on 2006-11-06
I'm open for all suggestions regarding the packages. For me, firefox and thunderbird fonts look both  okay (I think with Dapper patches fonts were still better), OpenOffice fonts look weird.

My settings from font-config are Autohinter, Automatic, Disable Bitmapped fonts. Medium hinting selected on GNOME font preferences.
I seem to use default fonts with GNOME (Sans family) and firefox (Serif family?).

/edit
I'm **not** overriding fonts config with local ~/.fonts.conf file

---

### Post by neo_reloaded on 2006-11-06
mlind, would you mind posting your complete fonts config file? 
If I understand correctly you do not have ~/.fonts.conf ?

I rolledback these patches to edgy's default libcairo anf xft. I will try these patches again today night(EST)

---

### Post by hugmenot on 2006-11-06
Hmm, it can only be Xft that has got problems. In Firefox all is fine and dandy; in Opera not.
BTW, I activated Pango as layout engine for Firefox. 
```
$ cat .mozilla/firefox/rc 
MOZ_DISABLE_PANGO=0
```

---

### Post by desperado666 on 2006-11-06
opera:config#UserPrefs|EnableCoreXFonts
deactivate 

Save 

opera:config#UserPrefs|EnableXftFonts
aktivate 

Save 

Restart Opera und now the text is antialised.

---

### Post by hugmenot on 2006-11-06
> **desperado666 said:**
> Restart Opera und now the text is antialised.

Draw Anti Aliased Fonts     x
Enable Core X Fonts	
Enable Xft Fonts	              x

Hm, already got that. Still I get selectively blurry characters.
Oh, and switching Pango off has only minor effects on kerning on this page (to the worse).

---

### Post by &#12465;&#12452;&#12488; on 2006-11-06
After adding the repositories and doing an aptitude upgrade, and the reconfigure stuff, I am unable to log back into GNOME. I'm currently running Firefox and OpenBox in the failsafe terminal mode.

I think the fonts are unable to render properly, so nothing really works now. I wish I knew exactly what packages that were installed, so I could reinstall the official packages.

---

### Post by hugmenot on 2006-11-06
> **&#12465 said:**
> After adding the repositories and doing an aptitude upgrade, and the reconfigure stuff, I am unable to log back into GNOME. I'm currently running Firefox and OpenBox in the failsafe terminal mode.

I think the fonts are unable to render properly, so nothing really works now. I wish I knew exactly what packages that were installed, so I could reinstall the official packages.

See posts 92 & 93 in this thread

---

### Post by &#12465;&#12452;&#12488; on 2006-11-06
libcairo2 was what I'd missed downgrading, thank you very much. :KS

---

### Post by msmeyer on 2006-11-06
> **hugmenot said:**
> Hmm, it can only be Xft that has got problems. In Firefox all is fine and dandy; in Opera not.
BTW, I activated Pango as layout engine for Firefox. 
```
$ cat .mozilla/firefox/rc 
MOZ_DISABLE_PANGO=0
```

That solved it for me! Firefox now again looks fine.

I agree that it might be that Xft has those problems. QT apps (which presumably use Xft, too) look blurry here, too, as does OpenOffice.

---

### Post by droebbel on 2006-11-06
As the libxft2 and libcairo2 packages do not work without the corresponding libfontconfig6, there should be a dependency on a suitable version. Otherwise, it is possible to make X unusable by installing libxft2 and libcairo2 only.

---

### Post by neo_reloaded on 2006-11-07
Ok!, again time for some screenshots this time a little more 
1)before applying patches 
2)after applying patches (with ~/.fonts.conf)
3)after applying patches (with out ~/.fonts.conf)
-- all using Corbel font for menus and consolas for terminal
4)after applying patches - with DejaVu sans condensed font. 

Conclusion: The smoothing patch makes it better(especially, web browser)

The behavior is different on fonts for example - Dejavu Sans Condensed looks far far better - but other fonts are still a bit crappy. 
And the effect of patches does not seem to be what it used to be in Dapper.
Looks like some base problem in libcairo or libxft - provided patches being the same.

Have a look :

---

### Post by mlind on 2006-11-07
I'll poke the libxft when I'll get some spare time, hopefully at the weekend.
Adding versioned shlib depends to freetype sounds reasonable to me too.

Here's my screenshot of firefox with current font patches:

---

### Post by neo_reloaded on 2006-11-07
Hm! Font settings are driving me crazy. Here's another setting/screenshot with patch applied.
this time I tried "Best shapes" on Font settings, followed by "BGR" on subpixel order.
Results weren't bad at all..or is it that it is almost 1:20 AM here?
:D

---

### Post by hugmenot on 2006-11-07
> **neo_reloaded said:**
> Hm! Font settings are driving me crazy. Here's another setting/screenshot with patch applied.
this time I tried "Best shapes" on Font settings, followed by "BGR" on subpixel order.
Results weren't bad at all..or is it that it is almost 1:20 AM here?
:D

It&#8217;s unlikely that BGR subpixel order is better on your screen unless you have a really rare LCD that doesn&#8217;t use RGB. Also the screenshot is done with RGB.
Corbel fell from grace with me after a long time using it. I suspect it has weird new-fangled hints that FreeType or whichever cannot cope with.

---

### Post by mata_svada on 2006-11-07
Is it just me or is font rendering in Edgy with the packages fron mlind's repository worse than with the patched debs avialable in this [thread]("http://ubuntuforums.org/showthread.php?t=180647")?

I've installed the debs for Dapper on Edgy and even though there are problems with dependencies they work and I do get better results.

[Edgy with mlind's packages]("http://www.aw-modell.at/mata/with_mlind's_packages.png")
[Edgy with the patched debs for Dapper]("http://www.aw-modell.at/mata/with_the_patched_debs_for_dapper.png")

Is there a way of getting better font rendering without broken dependencies?

---

### Post by hugmenot on 2006-11-08
> **mata_svada said:**
> I've installed the debs for Dapper on Edgy and even though there are problems with dependencies they work and I do get better results.


Interesting. The /only/ difference in the packages installed?
Konqueror uses Xft as well, right?

---

### Post by lord_nibbler on 2006-11-08
> **mata_svada said:**
> Is it just me or is font rendering in Edgy with the packages fron mlind's repository worse than with the patched debs avialable in this [thread]("http://ubuntuforums.org/showthread.php?t=180647")?


my font rendering was great before i did a apt-get upgrade yesterday.. some packets got upgraded an now all looks ugly.... :(

but i dont know what new package is the problem.. anyone with the same experiences?

best regards
lord nibbler

---

### Post by mlind on 2006-11-08
I'll try to roll new packages out on weekend. Problem is possibly with libxft2 patch.

---

### Post by lord_nibbler on 2006-11-08
> **mlind said:**
> I'll try to roll new packages out on weekend. Problem is possibly with libxft2 patch.

cool! thanx for your great work.

---

### Post by hugmenot on 2006-11-08
> **mlind said:**
> I'll try to roll new packages out on weekend. Problem is possibly with libxft2 patch.
Could be, but there is another Ubuntu-unrelated problem report
[http://www.nabble.com/Testing-new-LCD-rendering-mode-t2382905.html](http://www.nabble.com/Testing-new-LCD-rendering-mode-t2382905.html)

---

### Post by skorpio11 on 2006-11-08
Just wanted to state my appreciation for this thread.  OpenOffice is much improved now...

Thanks

---

### Post by hugmenot on 2006-11-09
> **skorpio11 said:**
> Just wanted to state my appreciation for this thread.  OpenOffice is much improved now...
Alright :confused: 
Stuff gets mystical now ...

---

### Post by marcog on 2006-11-09
> **VFiend said:**
> And we're done. Just put the results folder in a tar.gz and threw it up on a random free hosting service.

[http://senduit.com/6aae23](http://senduit.com/6aae23)

Let me know if there's anything else you'd like, and thanks again for the service you're doing

Any update on the amd64 packages? That link isn't working for me.

---

### Post by mlind on 2006-11-09
> **hugmenot said:**
> Could be, but there is another Ubuntu-unrelated problem report
[http://www.nabble.com/Testing-new-LCD-rendering-mode-t2382905.html](http://www.nabble.com/Testing-new-LCD-rendering-mode-t2382905.html)

Hmm.. I guess I should try building without Debian/Ubuntu changes from upsteam source package and see if same blurriness occurs.

---

### Post by mata_svada on 2006-11-10
[QUOTE="mlind"]Hmm.. I guess I should try building without Debian/Ubuntu changes from upsteam source package and see if same blurriness occurs.[/QUOTE]I`ll volunteer to test them, just tell me what to do.

---

### Post by hugmenot on 2006-11-10
> **mlind said:**
> Hmm.. I guess I should try building without Debian/Ubuntu changes from upsteam source package and see if same blurriness occurs.

What I meant to hint at was that it is possibly a problem upstream, i.e., with the patch itself.

---

### Post by Joe_Bishop on 2006-11-10
Mlind, thanks a lot. I have installed this packages from the repository about two weeks ago, and today I have upgraded them. It seems to me, older version draw windows fonts a little better than new. For example, "r", "k" and several letters from Cyrillyc set with Verdana font family have some artifacts. But native Linux fonts look better.
[http://www.ubuntuforums.org/attachment.php?attachmentid=19134&stc=1&d=1163193796](http://www.ubuntuforums.org/attachment.php?attachmentid=19134&stc=1&d=1163193796)

---

### Post by dparadinha on 2006-11-11
hello! i'm sorry to pose the question like this, but... what's the real conclusion of this forum?
nevertheless, thanks for all that have been working hard!

---

### Post by sledgehammer89 on 2006-11-13
Great, thanks for this patches!!

I have only 2 problems now:

- the character "8" in Tahoma (look at these "8"'s in the adressbar and the folder on the top, there is one unusual pixel)
- openoffice

see the screenshots.

Thanks, with regards,

SH

PS: yes, I mixed aliased and non-aliased fonts with kcontrol (from KDE), because I like non-aliased small fonts more then small aliased fonts ;)

---

### Post by hugmenot on 2006-11-13
> **sledgehammer89 said:**
> 
- the character "8" in Tahoma (look at these "8"'s in the adressbar and the folder on the top, there is one unusual pixel)


Well you have aliased fonts. The fuzzy blurry stuff is called antialiased.

But back on topic: Perhaps this is the explanation for problems with Windows fonts?
[http://article.gmane.org/gmane.comp.fonts.freetype.user/1997](http://article.gmane.org/gmane.comp.fonts.freetype.user/1997)

---

### Post by Kandinsky on 2006-11-14
Just a quick question please.

How can I downgrade to the original packages again?

I would like to remove the stuff installed with dist-upgrade.

Thanks,

Kandinsky

---

### Post by sledgehammer89 on 2006-11-14
> **hugmenot said:**
> Well you have aliased fonts. The fuzzy blurry stuff is called antialiased.

But back on topic: Perhaps this is the explanation for problems with Windows fonts?
[http://article.gmane.org/gmane.comp.fonts.freetype.user/1997](http://article.gmane.org/gmane.comp.fonts.freetype.user/1997)

I think it is a bit related ;) If it's fuzzy without aliased turned off, then it looks not really good with aliased on. Please have a look on this link:
[http://en.opensuse.org/Optimal_Use_of_MS_TrueType_Core_Fonts_for_a_KDE_Desktop_on_SuSE]("http://en.opensuse.org/Optimal_Use_of_MS_TrueType_Core_Fonts_for_a_KDE_Desktop_on_SuSE")
> There are lots of pics on the web with Tahoma 8, all of them have a broken rendering of the character "8". The bottom circle always has one pixel too many. If anyone knows how to fix it then please append the fix on this page or link to it.

I see with Tahoma Bold 8 another bad character: "[FONT="Tahoma"][SIZE="1"]**x**[/SIZE][/FONT]" (the line to top right edge in the "x" character)

With aliased on, Tahoma 8 doesn't look equal like on Windows. I see it, for example, on a bold "S" character.

xorg.conf, fonts.conf are configured with 96dpi, as X starts with 96dpi

Thanks, bye

SH

---

### Post by hugmenot on 2006-11-14
> **sledgehammer89 said:**
> I think it is a bit related ;) If it's fuzzy without aliased turned off, then it looks not really good with aliased on. Please have a look on this link:
Again, you deactivate anti-alias hence you get aliased fonts on screen. Another term for that is monochrome fonts because only black and white is used (no gray levels).

Now, monochrome only looks good with fonts that have quality hints embedded. There is no way to optimally render characters on a coarse pixel grid without specific info about what is important in a letter. Hence the hinting. Of course you need to interpret the hints correctly, and in the link I provided it is stated that this interpretation (hinting or byte-code interpretation) is broken a bit currently. You have to wait and see when it&#8217;s fixed. (Or go back to the old style.)

BTW, after working on a Mac box the whole day I must say that OSX definitely is not the "gold standard" we are aspiring to. I could only stand it because I was seated fairly far from the screen (which was big). I thought OSX would perform better in that arena.

---

### Post by VFiend on 2006-11-15
> **marcog said:**
> Any update on the amd64 packages? That link isn't working for me.

Looks like mlind didn't do anything yet, I'll send him a private message then

---

### Post by mercurysquad on 2006-11-16
> **mlind said:**
> Thanks for the feedback. Do you think results are better with **experimental** packages than with packages in **fonts** repository?

If so, I should probably make experimental packages as default.

How can I go back to 2.1 patches? Right now I have ubuntu2.2 patches and I don't like it....

I tried apt-get install libcairo2=1.2.4-1ubuntu2.1 but it can't find the package...

---

### Post by mercurysquad on 2006-11-16
> **mata_svada said:**
> Is it just me or is font rendering in Edgy with the packages fron mlind's repository worse than with the patched debs avialable in this [thread]("http://ubuntuforums.org/showthread.php?t=180647")?


Exactly my problem. Before the 2.2 patches, all was awesome. Now it's not as awesome as it should be..

---

### Post by lord_nibbler on 2006-11-16
> **mercurysquad said:**
> How can I go back to 2.1 patches? Right now I have ubuntu2.2 patches and I don't like it....

I tried apt-get install libcairo2=1.2.4-1ubuntu2.1 but it can't find the package...

i have the same problem, any chance to geht the "old" packages back?

---

### Post by xska on 2006-11-18
Yeah, old ubuntu2.1 packages back would be cool. I have a lot of artifacts in russian fonts, for example letter "&#1099;" totally messes up text display in some applications. And this problem has surfaced after the last automatic upgrade.

---

### Post by hugmenot on 2006-11-18
Mlind, I think we built from CVS a little early. It is quite in flux currently with respect to work on auto-hinting, byte-code interpreter and LCD filtering in the last days.

We could try to build CVS again or to revert to the old style in the repo.

EDIT: Good news. I built freetype2 CVS and at least my problems were fixed -> screenshot. Now there&#8217;s even the [possibility to switch LCD algos]("http://article.gmane.org/gmane.comp.fonts.freetype.devel/4338")

---

### Post by xska on 2006-11-18
Here's an attachment that shows how the bug with russian '&#1099;' letter looks like.

Take a look at the last part of the Epiphany URL bar. There is actually three letters '&#1099;' typed in, though they show as something undecipherable.

---

### Post by Joe_Bishop on 2006-11-19
hegemenot, when the new versions of packages will be placed in the repo?

---

### Post by Neo40 on 2006-11-19
I did a fresh install of Edgy and after I installed the patches by adding the sources as it says on the 1st post of this thread, I'm now unable to get X working: After reboot, I only see the cursor and a brown background.
How can I reinstall the originals libcairo2 and libxft?

Thanks

EDIT: Nevermind. I forgot to do: apt-get dist-upgrade. Problem solved!

---

### Post by mlind on 2006-11-19
alright, I'll put 2.1 version back to fonts repository and start building freetype on experimental more frequently.

---

### Post by hugmenot on 2006-11-19
Cool. And this was the problematic issue:

```
2006-11-13  David Turner  <david@freetype.org>

        * src/truetype/ttinterp.c (FIX_BYTECODE): Undefine.  The interpreter
        `enhancements' are still too buggy for general use.
```

---

### Post by mata_svada on 2006-11-20
I updated to the new packages today and I get slightly better results than before but with the dapper-packages (from [here](http://ubuntuforums.org/showthread.php?t=180647)) it still is by far better. I just need to install libfreetype6-2.1.10patched.

Is it because of the different versions or because of different patches and if it is because of the versions how can I make Edgy not to complain about the older version of libfreetype6?

Cheers,
Matej

---

### Post by nubutu on 2006-11-20
Hi.

After playing a while with several tutorials, applying patches and so on, I found that the only way to have my fonts as they used to be in Dapper is after installing the ATI binary driver. Now, this shouldn't affect, but the thing is it does. It probably has something to do with some configuration files its installation changes/deactivates, I'm not able to tell. If I go back to the open source driver, the fonts get crap again. Would somebody have any idea about how to keep the way fonts are rendered when using fglrx, or why does this happen?

Thanks

---

### Post by xska on 2006-11-21
how do I manually downgrade to previous version? Or should I just wait till the update manager tells me to?

---

### Post by reacocard on 2006-11-21
> **xska said:**
> how do I manually downgrade to previous version? Or should I just wait till the update manager tells me to?

Just open synaptic, find the package, and use Package -> Force Version to downgrade.

---

### Post by ProtecT on 2006-11-23
I applied patches and got good fonts. But in OpenOffice fonts look ugly :-k.
What you can offer me to do with OpenOffice?

That i have now:

---

### Post by gentoofrm on 2006-11-23
1) sudo dpkg-reconfigure fontconfig

then choose "native", 
then choose "automatic", 
then choose "yes".

2) (Gnome Panel) System -> Preferences -> Font -> Details

Smoothing (none)
Hinting (full)

3) log out & log in

[http://www.linuxjournal.com/article/9166](http://www.linuxjournal.com/article/9166)

---

### Post by oobuntoo on 2006-11-24
A few days ago, there were updates for some font-related library packages, can't remember which, and now the ugly, blurry, superbold fonts are back. On top of that, a bunch of fonts I installed don't show up anymore for Firefox and other appplications.

---

### Post by happy-and-lost on 2006-11-24
Installed these packages, fonts became blurry. Uninstalled packages, fonts worse than before I installed the packages :S Any suggestions as to how to get Edgy's default Subpixel LCD setting back?

---

### Post by floke on 2006-11-24
I had problems with my fonts in Edgy for OOo - not dire but scruffy. One solution, which had worked for me, is to install the KDE desktop (ie Kubuntu). The fonts in this are great (at least for me)!

Steve

---

### Post by ThrobbingBrain66 on 2006-11-26
mlind, just as a side note, i've been trying to grab your key (937215FF) for a few days now and the request times out every single time.

it's worked before, but the last few days have been no joy.

---

### Post by mlind on 2006-11-26
> **oobuntoo said:**
> A few days ago, there were updates for some font-related library packages, can't remember which, and now the ugly, blurry, superbold fonts are back. On top of that, a bunch of fonts I installed don't show up anymore for Firefox and other appplications.

Try using 'experimental' repository
```

deb http://www.elisanet.fi/mlind/ubuntu edgy experimental

```

There were few requests to get older font packages back, that's probably why superbolded fonts are back too.

---

### Post by mlind on 2006-11-26
> **happy-and-lost said:**
> Installed these packages, fonts became blurry. Uninstalled packages, fonts worse than before I installed the packages :S Any suggestions as to how to get Edgy's default Subpixel LCD setting back?

This should do it
```

sudo aptitude install libfreetype6=2.2.1-5 libcairo2=1.2.4-1ubuntu2 libxft2=2.1.10-1ubuntu1

```


> **ThrobbingBrain66 said:**
> mlind, just as a side note, i've been trying to grab your key (937215FF) for a few days now and the request times out every single time.

it's worked before, but the last few days have been no joy.

Try this
```

gpg --recv-keys 937215FF --keyserver subkeys.pgp.net

```

---

### Post by ThrobbingBrain66 on 2006-11-26
> **mlind said:**
> 
Try this
```

gpg --recv-keys 937215FF --keyserver subkeys.pgp.net

```

no dice. i've tried a few different methods to get your key:

```
gpg --keyserver subkeys.pgp.net --recv 937215FF && gpg --export --armor 937215FF | sudo apt-key add -
```

```
gpg --recv-keys 937215FF --keyserver subkeys.pgp.net
```

```
gpg --recv-keys 937215FF && gpg --export --armor 937215FF | sudo apt-key add -
```

and none of them work.  they all either time-out or fail and i HAVE been able to get other keys to import.  any other ideas?

---

### Post by hugmenot on 2006-11-26
> **ThrobbingBrain66 said:**
> no dice. i've tried a few different methods to get your key:

```
gpg --keyserver subkeys.pgp.net --recv 937215FF && gpg --export --armor 937215FF | sudo apt-key add -
```

```
gpg --recv-keys 937215FF --keyserver subkeys.pgp.net
```

```
gpg --recv-keys 937215FF && gpg --export --armor 937215FF | sudo apt-key add -
```

and none of them work.  they all either time-out or fail and i HAVE been able to get other keys to import.  any other ideas?

Yes, you&#8217;re firewalled on non-http ports.
Get a web-interface and copy the key into a file.

---

### Post by ThrobbingBrain66 on 2006-11-26
> **hugmenot said:**
> Yes, you&#8217;re firewalled on non-http ports.
Get a web-interface and copy the key into a file.

i have to respectfully disagree because i use the same format:

```
gpg --keyserver subkeys.pgp.net --recv xxxxxxxx && gpg --export --armor xxxxxxxx | apt-key add -
```

to get trevino's beryl-svn repo and seveas' repo and they go through without a hitch

and if it is as you say it is, i guess i dont understand what you mean by getting a web-interface, etc.

---

### Post by hugmenot on 2006-11-26
> **ThrobbingBrain66 said:**
> i have to respectfully disagree because i use the same format:

```
gpg --keyserver subkeys.pgp.net --recv xxxxxxxx && gpg --export --armor xxxxxxxx | apt-key add -
```

to get trevino's beryl-svn repo and seveas' repo and they go through without a hitch

and if it is as you say it is, i guess i dont understand what you mean by getting a web-interface, etc.

I have no idea why you have problems, I know that openpgp works over a non-80 non-443 port, though.

Try this: [http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x937215FF](http://pgp.mit.edu:11371/pks/lookup?op=vindex&search=0x937215FF)

---

### Post by ThrobbingBrain66 on 2006-11-26
i tried to use that address with wget to obtain the key, but that didnt work.  to be honest, i have no idea what you want me to do with that link.  please excuse my thick-headedness.

---

### Post by mlind on 2006-11-26
> **ThrobbingBrain66 said:**
> no dice. i've tried a few different methods to get your key:

If you cannot obtain the key from public keyserver for some reason, use the link [http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x937215FF](http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x937215FF), manually save the armored gpg key to a file, then import.

---

### Post by ThrobbingBrain66 on 2006-11-26
> **mlind said:**
> If you cannot obtain the key from public keyserver for some reason, use the link [http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x937215FF](http://pgp.mit.edu:11371/pks/lookup?op=get&search=0x937215FF), manually save the armored gpg key to a file, then import.

that did the trick.  until now i had not run into a situation like that, so i thank you for your patience.

---

### Post by Joe_Bishop on 2006-11-28
Errrr....
After last update cyrillic fonts in Gtk applications became giant, although in Qt they are still looking normal. See attachment for details.
----------------------
For comparison, I have also applied Windows XP screenshot.
I have set 96dpi everywere, and use the same font settings in Firefox for Ubuntu and Windows (13-16, Arial, Times New Roman).

---

### Post by mlind on 2006-11-28
yeah, I'm quite sure it's not problem with the packages, but bug in  freetype HEAD. I'll roll-up new packages in a day or two, depending on cvs activity.

---

### Post by WorLord on 2006-11-30
WOW.  

Applied patch.  Went to Fonts preferences, went to Details button.

96DPI + Subpixel Rendering + Slight Hinting + RGB = absolutely STUNNING results.  They've never looked this good in Ubuntu.  They look almost as good (to my eyes) as a Mac, and certainly better than ClearType (my gripe against that is that Arial doesn't actually look like Ariel with it turned on.  This looks like Ariel, but done RIGHT.)

Also, serif fonts especially look good, and they've always looked rather poor in Ubuntu.  

If anyone wants to see, tell me how to add screenshots.

---

### Post by mlind on 2006-11-30
> **WorLord said:**
> WOW.  

Applied patch.  Went to Fonts preferences, went to Details button.

96DPI + Subpixel Rendering + Slight Hinting + RGB = absolutely STUNNING results.  They've never looked this good in Ubuntu.  They look almost as good (to my eyes) as a Mac, and certainly better than ClearType (my gripe against that is that Arial doesn't actually look like Ariel with it turned on.  This looks like Ariel, but done RIGHT.)

Also, serif fonts especially look good, and they've always looked rather poor in Ubuntu.  

If anyone wants to see, tell me how to add screenshots.

You can just press print-screen button, scale image a bit with gimp and attach it as a .png file to your posts.

Did you install packages from **fonts** or **experimental** repository?

---

### Post by hugmenot on 2006-11-30
[QUOTE=WorLord;1828546]This looks like Ariel, but done RIGHT.

Does that mean that you use Helvetica now? ;)

But I agree. Results are very pleasing by now. I also use a serif for applications.
This is better than OSX.

---

### Post by WorLord on 2006-11-30
> **mlind said:**
> You can just press print-screen button, scale image a bit with gimp and attach it as a .png file to your posts.

I know how to make the screenshot... I didn't at all see the attachment button!  

> Did you install packages from **fonts** or **experimental** repository?

Fonts!  

There's an experimental??  Does it help any?  Hard to imagine better...

> Does that mean that you use Helvetica now?

HA!

---

### Post by mlind on 2006-12-01
> **WorLord said:**
> 
There's an experimental??  Does it help any?  Hard to imagine 


IMO libfreetype6, libcairo2, libxft2 packages on experimental repository improve font quality even better, but that could be just me :mrgreen: 
If you plan to try experimental packages and then later decide to switch back, remember to downgrade **all** three packages, including libfreetype6.

---

### Post by hugmenot on 2006-12-01
> **WorLord said:**
> I know how to make the screenshot... I didn't at all see the attachment button!  

There's an experimental??  Does it help any?  Hard to imagine better...


Good that you didn&#8217;t scale the screenshot, cause that&#8217;d be pointless.
Installing from experimetal will give you better contrast and sharper edges. It could be that you actually don&#8217;t see it as an improvement consiudering that you like "slight hinting". This field is highly susceptible to personal taste.

I updated the first post to highlight the two options.

For Arial, it was a joke. Arial is seen as ripped off of Helvetica.
[http://www.engagestudio.com/helvetica/](http://www.engagestudio.com/helvetica/)

---

### Post by WorLord on 2006-12-01
> **hugmenot said:**
> Good that you didn&#8217;t scale the screenshot, cause that&#8217;d be pointless.

Yeah, I zoomed it in and looked at it.  But I find every form of antialiasing to be sloppy zoomed in.


> Installing from experimetal will give you better contrast and sharper edges. It could be that you actually don&#8217;t see it as an improvement consiudering that you like "slight hinting".

Well.  I have it set to slight because I tried all of the possible combinations.  ALL of the other hinting methods looked - like many here often report - very problematic for me.  They were blurry, as if (when it came to fonts) I was seeing things through a camera lens or projector, but the lens wasn't quite focused as sharply as it should have been.  Many stems appeared uneven - some stems were thinner/lighter than others, which was really offputting considering that often this was the case in the same letter (uppercase sans-serif "M" is a good example).  The spacing on all other methods was also uneven and seemingly random: Double lowercase sans-serif "L"'s were close together, but other stems were wider apart. And when bolded (as you can see, Banshee bolds what its playing), I notice lowercase "e"'s didn't appear to have a hole in them at all - just a mass of black.  

Imagine my surprise when changing to "slight" hinting, and finding most or all of these problems just vanishing.


>  I updated the first post to highlight the two options. 

I definitely want sharper fonts.  These are a tad blurry and color-bleedy (small black text on white backgrounds, especially, its really easy to tell that its anti-aliased with colors), so if this can be improved even further, I'd LOVE that.

***Edit: A few moments Later***

I've installed the experimental packages, though I had to do it manually because there is an MD5SUM mismatch on the libfreetype6 package.  I like what I see: the dots over lowercase "i"s are now very clearly separated (they weren't before).  Everything looks better than it did, and I'd think that'd be a difficult feat to accomplish.  For some reason, though, "Slight" hinting still produces the best results to my eye.  "None" just sucks out loud; "Medium" and "Full" hinting both produce (if you can believe this) pixelated diagonal stems (capital "W" and "A" are easiest to notice), and "Full" seems to produce *really* thin stems and very strange-looking lowercase "E"s.  And, firefox now looks kind of off (OpenOffice looks atrocious, too, but I hear that's going around with these patches.)

I definitely like experimental better.  Thanks for the heads up on that!  (Screenshot of these Experimental packages on the same machine, with the same music player, attached).

> For Arial, it was a joke.

I know; that's why I laughed.  (Wasn't Arial invented to be Helvitica without the patent?  I'm not all that up on my font history.)

---

### Post by WorLord on 2006-12-01
Even further updates: 

Firefox didn't look like it was rendering fonts properly.  As one of the people who lobbied to have Firefox turn Pango off unless it was absolutely necessary, I decided to see if Pango-enabled FF would fix my problem (hoping that the atrociously slow rendering times of web pages with Pango were fixed).  

I did this (for all users) by modifying /usr/bin/firefox.  I found and commented out the following stanza: 

```
# if [ "x${MOZ_DISABLE_PANGO}" = x ]; then
#     if egrep '^(bn|gu|hi|kn|ml|mr|ne|pa|si|ta|te)_' \
# 	/var/lib/locales/supported.d/*[^~] >/dev/null 2>&1; then
# 	MOZ_DISABLE_PANGO=0
#     else
# 	MOZ_DISABLE_PANGO=1
#     fi
#     export MOZ_DISABLE_PANGO
# fi
```

And then adding right under it: 

```
MOZ_DISABLE_PANGO=0
export MOZ_DISABLE_PANGO
```

FF now looks just as awesome as everything else.  Still slower, but not nearly the catastrophic slowness that Dapper's FF/Pango combo was.

Also, with the new Experimental packages, OO.o looks really good.  In fact, just about as great as everything else!!  That's totally awesome.  Thank you guys so much.

---

### Post by mata_svada on 2006-12-05
I just wanted to mention that I installed the packages for Edgy today and I must say that it is the same (unbelievably great) font-rendering quality as I had under Dapper. None of [these Problems]("http://www.ubuntuforums.org/showpost.php?p=1728517&postcount=134") occour anymore.

Thank you and keep up the good work!

---

### Post by prokoudine on 2006-12-05
Btw, did anyone try this repo on Feisty?

---

### Post by mlind on 2006-12-05
> **prokoudine said:**
> Btw, did anyone try this repo on Feisty?

I haven't tried Feisty yet, but I reckon edgy and feisty aren't binary compatible anymore.
Feel free to try though :mrgreen: 

btw. you could try rebuilding the packages if binaries cannot be installed.

---

### Post by marcele on 2006-12-06
> **reacocard said:**
> For edgy, the following produces the best results for me.

after installing the packages, do a
```
sudo dpkg-reconfigure fontconfig-config
```
select "native","automatic" and "no", in that order.
do a
```
sudo dpkg-reconfigure fontconfig
```
open System-> Administration-> Font, select "subpixel smoothing", then go to "details".
Select "Subpixel", "Full", and "RGB", in that order.
Restart X and enjoy the improved fonts.

Man does that ever look better! Thanks for this :) Gnome-main-menu actually looks great now ! (I'm using edgy)

---

### Post by russbuss on 2006-12-16
First off, I just installed mlind's packages and they have made my font rendering so much better.  Thanks for doing this; the font rendering in Edgy (and Ubuntu in general) was really starting to drive me nuts.  These packages are a huge improvement and I would love to see them made standard for Ubuntu.

Regarding font rendering in FF:

> **WorLord said:**
> 
I did this (for all users) by modifying /usr/bin/firefox.  I found and commented out the following stanza: 

```
# if [ "x${MOZ_DISABLE_PANGO}" = x ]; then
#     if egrep '^(bn|gu|hi|kn|ml|mr|ne|pa|si|ta|te)_' \
# 	/var/lib/locales/supported.d/*[^~] >/dev/null 2>&1; then
# 	MOZ_DISABLE_PANGO=0
#     else
# 	MOZ_DISABLE_PANGO=1
#     fi
#     export MOZ_DISABLE_PANGO
# fi
```


I tried to edit /usr/bin/firefox, but could not find the above-mentioned lines in it.  I am running FF 2.0, so could this have anything to do with those lines not being there?  I do agree that the font rendering in FF is not the same as it is for everything else.  It would be nice to at least see of this change improves anything.

---

### Post by Ruth Lazkoz on 2006-12-18
Please can you give me instructions to:

1) download the source packages 
2) compile and install

I am pretty new to ubuntu/linux, and I would be very much like to improve fonr rendering

---

### Post by hugmenot on 2006-12-18
Ah, you already found this thread.

To get the source packages use apt-get source libfreetype6 libcairo2 libxft2

Why do you need to compile them though? Which is your exact Ubuntu flavor?

---

### Post by Ruth Lazkoz on 2006-12-18
> **hugmenot said:**
> Ah, you already found this thread.

To get the source packages use apt-get source libfreetype6 libcairo2 libxft2

Why do you need to compile them though? Which is your exact Ubuntu flavor?

I guess I have to because the amd64 binaries do not exist in the repository

---

### Post by zigford on 2006-12-18
I use amd64 too, No chance that could be added to the repos?

---

### Post by hugmenot on 2006-12-18
> **Ruth Lazkoz said:**
> I guess I have to because the amd64 binaries do not exist in the repository

That&#8217;s true actually. We should do something about that.
Until that happens you could try to build on your machine; it should be painless.

First get the stuff needed for building these three packages
```
sudo apt-get build-dep libfreetype6 libcairo2 libxft2
```
then navigate to some suitable tmp directory and get the actual source packages```
apt-get source libfreetype6 libcairo2 libxft2
```
There is a toggle for apt-get (--compile) that builds the packages after downloading but I usually go into the created directories and start building from there; one example:
```
~/src/X/fonts$ cd freetype-2.2.1+cvs20061216/
~/src/X/fonts/freetype-2.2.1+cvs20061216$ dpkg-buildpackage -rfakeroot -b
```

The finished packages are dropped into the parent folder (i.e., for me ~/src/X/fonts/)

Thats&#8217;s how I do it. Mlind has a procedure involving the more automated pbuilder system. Mine is more simple.

---

### Post by mlind on 2006-12-18
I promised to upload amd64 packages a while ago, but somehow I haven't got it done yet, sorry.
If someone provides me the amd64 binaries, with a build log and (and hopefully gpg signed .changes and .dsc files), I'll finally try to make the upload.

---

### Post by zigford on 2006-12-19
> **gryan said:**
> I was able to get the source package for freetype from the experimental repository, but when I attempt to get the source for cairo, it conks out with the following message:

$ apt-get source libcairo2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 2905kB of source archives.
Get:1 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (dsc) [896B]
Get:2 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (tar) [2883kB]
Get:3 [http://www.elisanet.fi](http://www.elisanet.fi) edgy/experimental libcairo 1.2.4-1ubuntu2.2 (diff) [21.7kB]                                             
Fetched 2883kB in 1m55s (25.0kB/s)                                                                                                   
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.dsc](http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.dsc)  MD5Sum mismatch
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.diff.gz](http://www.elisanet.fi/mlind/ubuntu/pool/experimental/libc/libcairo/libcairo_1.2.4-1ubuntu2.2.diff.gz)  MD5Sum mismatch
E: Failed to fetch some archives.

The fact that I'm running AMD64 shouldn't make a difference, but I mention it in case I'm wrong. :-)

- George

I'm getting very similar messages to this now.  Does the checksum need to be updated again?

Thanks

---

### Post by mlind on 2006-12-19
> **zigford said:**
> I'm getting very similar messages to this now.  Does the checksum need to be updated again?

Thanks

thanks, fixed once again.

---

### Post by Ruth Lazkoz on 2006-12-19
Hi,

I generated those binaries following your instructions, but they are to big. How can I send them to you? 

As I asaid am I am very new to ubuntu. I have seen the folder with the files can be shared (over the web)? Maybe you can email ma at [email]wtplasa@lg.ehu.es[/email] to give me advise.

Anyway, I installed the files and saw no improvement on font rendering, so I wonder what I am doing wrong.

Ruth

---

### Post by hugmenot on 2006-12-19
run this

sudo dpkg-reconfigure fontconfig-config

and choose subpixel on the second screen.
You can also consult the first post of this thread.

---

### Post by benjaminzsj on 2006-12-19
Hello. Since the Minefield alpha is out and it uses cairo now, I wonder how your great packages work with it. :) I tried Minefield and found a bit different with previous version in terms of font rendering.

---

### Post by zigford on 2006-12-19
Hey, the fonts definatly look alot nicer.  How does the technology enfringe on another technology when both were created independantly?  Will the patches ever be merged upstream?

---

### Post by mlind on 2006-12-22
> **zigford said:**
> Hey, the fonts definatly look alot nicer.  How does the technology enfringe on another technology when both were created independantly?  Will the patches ever be merged upstream?

software patents I guess. It's unlikely that patches will be merged upsteam until patent issues are solved.

---

### Post by rosvall on 2006-12-22
What's the status with those amd64 packages?

 I was going to compile them my self, but when running sudo apt-get build-dep libfreetype6 libcairo2 libxft2 I'll get an error "Could not open file /var/lib/apt/lists/www.elisanet.fi_mlind_ubuntu_dists_edgy_fonts_source_Sources - open (2 No such file or directory)"

I have added these:

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts

in my sources.list

---

### Post by mlind on 2006-12-22
> **rosvall said:**
> What's the status with those amd64 packages?

 I was going to compile them my self, but when running sudo apt-get build-dep libfreetype6 libcairo2 libxft2 I'll get an error "Could not open file /var/lib/apt/lists/www.elisanet.fi_mlind_ubuntu_dists_edgy_fonts_source_Sources - open (2 No such file or directory)"

I have added these:

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts

in my sources.list

No amd64 packages yet, I haven't received any.

Did you invoke *aptitude update* before doing that?

---

### Post by rosvall on 2006-12-23
When I tryed "sudo apt-get update" it gives following error:

Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/edgy/Release](http://www.elisanet.fi/mlind/ubuntu/dists/edgy/Release)  Unable to find expected entry  fonts/binary-amd64/Packages in Meta-index file (malformed Release file?)

But now I tryed sudo aptitude update and it seems to work :)...
I'll compile those amd64 packages now :)

---

### Post by rosvall on 2006-12-23
Actually, it still does't work... 

sudo apt-get build-dep libfreetype6 libcairo2 libxft2

gives error:

 Could not open file /var/lib/apt/lists/www.elisanet.fi_mlind_ubuntu_dists_edgy_fonts_source_Sources - open (2 No such file or directory)

---

### Post by mlind on 2006-12-23
Not sure what's the problem here, I never use apt-get build-dep myself. Use other method to install the build-depends.

btw. does the local file /var/lib/apt/lists/www.elisanet.fi_mlind_ubuntu_dists_edgy_fonts_source_Sources exist and look okay to you?

---

### Post by rosvall on 2006-12-23
Amd64 packages for edgy can be found here: [http://koti.mbnet.fi/coyctecm/ubuntu/fonts/](http://koti.mbnet.fi/coyctecm/ubuntu/fonts/)

Mlind: you can add those in your repos if you like, they should work fine, I'm using them now..

---

### Post by NeoChaosX on 2006-12-25
> **hugmenot said:**
> 

To reduce the superbold appearance it might help to switch the autohinter off for bold faces.
This can be done by adding some lines in the .fonts.conf file in the user home directory or in the system-wide /etc/fonts/fonts.conf. A complete user file is attached to this post. 
```
<match target="font">
 <test name="weight" compare="more"><const>medium</const></test>
 <edit mode="assign" name="autohint"><bool>false</bool></edit>
</match>
```
This isn't working for me in Kubuntu. I enter those lines in my .fonts.conf and I'm still getting superbolded fonts, especially when viewing sites that use fonts like Tahoma and Verdana.

---

### Post by elcasey on 2006-12-26
I had to switch back to my original fonts.conf to keep it from being waaay too blurry for me (you did back the original file up, right?).

I followed the steps in this thread because, quite frankly, the fonts in apps like XMMS and NeroLinux look like sh*t now. Anything that uses the (what I call) "old school UNIX" menus has fonts that are absolutely atrociously rendered. How can I fix *this* rather than jacking around with my system-wide fonts (I wish I'd never messed with them in the first place, to be honest - I can feel the eye strain beginning already).

---

### Post by elcasey on 2006-12-27
I was able to fix both the GNOME fonts and the "non-WM" fonts in applications such as XMMS, NeroLinux and Emacs! 

To start, do a [FONT="Courier New"]gksudo gedit /etc/X11/xorg.conf[/FONT] (or use your editor of choice).

Then, comment out (#) all the entries in the "Section "Files"" area of xorg.conf.

Paste in these new values:
```
Section "Files"
              # ADDED
              FontPath        "/usr/share/fonts/X11/misc"
              FontPath        "/usr/share/fonts/X11/cyrillic"
              FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
              FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
              FontPath        "/usr/share/fonts/X11/Type1"
              FontPath        "/usr/share/fonts/X11/100dpi"
              FontPath        "/usr/share/fonts/X11/75dpi"
              FontPath        "/usr/share/fonts/X11/misc"

```
Do not paste in "Section "Files"" if you didn't comment out the original. This will fix the blurriness of the fonts in GNOME *and* it will crisp up the fonts in "generic" apps that don't use your WM fonts (such as Emacs X11, NeroLinux, etc).

Now if I can just figure out how to de-super-bold my window titles! :rolleyes:

Huge thanks and all the credit goes to *violot* of #ubuntuforums on Freenode.

---

### Post by Joe_Bishop on 2006-12-30
Hey, what about gecko browsers? They are still look wrong.
See the example: Opera renders the page near to as it should be, while in firefox fonts are too great.

---

### Post by rebeldevel on 2006-12-31
[http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) doesn't work anymore! (open this link in your browser...)

Where else can I get the packages? :mrgreen:

---

### Post by diebels on 2007-01-01
Vow! This is really good font rendering. Thanks!

---

### Post by chiklit on 2007-01-01
Is there anything that can be done to get the fonts in CrossOver to not look like this...

---

### Post by mercurysquad on 2007-01-03
Hi ppl,

I just made patched debs for Feisty Fawn (x86)...
They are here: [http://www.ubuntuforums.org/showthread.php?t=330579](http://www.ubuntuforums.org/showthread.php?t=330579)

mlind, you might want to create a repository for feisty and put those in, as I tried changing edgy to feisty in your repo URL and it didn't work. I have all the other packages also (-dev, -docs blah blah) if needed.

---

### Post by mercurysquad on 2007-01-03
> **chiklit said:**
> Is there anything that can be done to get the fonts in CrossOver to not look like this...

Seems like CrossOver is using the Motif gui toolkit instead of GTK/Qt .... in which case there's nothing you/we can do (I think). Same with Mathematica, e.g., and it is closed-source with Motif statically compiled in so there REALLY is nothing we can do. ](*,)

---

### Post by islyusar on 2007-01-03
I used the "Flavor 2" patch because it was named "a newer one" in the original post. My fonts started looking worse: all symbols got some strange blueish glow. I used Ubuntu 6.10, default fonts, Acer AL1951 monitor and did my best to follow the instructions. I applied the "Flavor 1" patch then, and the fonts lost the blueish glow, but became blurry. I did not like much the way Ubuntu fonts looked before (that's why I got here), but I definitely did not like the way they looked after the patches. So I had to downgrade to the original Edgy versions of Cairo and Xft using Synaptic.

---

### Post by mercurysquad on 2007-01-03
It is a matter of taste.
I can't live without the old flavour 1 (the realllly old one).
Which is also the flavor of the patched debs I linked above ^

---

### Post by islyusar on 2007-01-03
Personally, for me, it was not about taste. It hurt my eyes. Literally.

---

### Post by mlind on 2007-01-03
> **mercurysquad said:**
> 
mlind, you might want to create a repository for feisty and put those in, as I tried changing edgy to feisty in your repo URL and it didn't work. I have all the other packages also (-dev, -docs blah blah) if needed.

There's no feisty packages yet, I'm waiting for libcairo2 sync from Debian.

---

### Post by hugmenot on 2007-01-04
I doesn&#8217;t hurt mine. How come? Care to post a screenshot?
There&#8217;s the possibility that you have suboptimal results.

---

### Post by ptr^v on 2007-01-05
> **mlind said:**
> Not sure what's the problem here, I never use apt-get build-dep myself. Use other method to install the build-depends.

btw. does the local file /var/lib/apt/lists/www.elisanet.fi_mlind_ubuntu_dists_edgy_fonts_source_Sources exist and look okay to you?

hello, i have same error :S what other method do you mean?

this is the files /var/lib/apt/lists/

lock     [www.elisanet.fi_mlind_ubuntu_dists_edgy_Release](www.elisanet.fi_mlind_ubuntu_dists_edgy_Release)
partial  [www.elisanet.fi_mlind_ubuntu_dists_edgy_Release.gpg](www.elisanet.fi_mlind_ubuntu_dists_edgy_Release.gpg)


i dont know how to install this exactly, i have AMD64....


All what i know is i installed windows fonts and configure files, now this topic is to improve those fonts more right? i read this entire topic and i see screenshot with good fonts i also want that](*,) 

thanks

---

### Post by ptr^v on 2007-01-05
> **rosvall said:**
> Amd64 packages for edgy can be found here: [http://koti.mbnet.fi/coyctecm/ubuntu/fonts/](http://koti.mbnet.fi/coyctecm/ubuntu/fonts/)

Mlind: you can add those in your repos if you like, they should work fine, I'm using them now..

how do you install those? thanks!

---

### Post by hugmenot on 2007-01-05
Do you have the correct apt source line? And did you update the apt-cache?
```
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts
```or ```
deb-src http://www.elisanet.fi/mlind/ubuntu edgy experimental
```

BTW, **Cairo 1.2.6** just arrived on my Feisty machine...

---

### Post by ptr^v on 2007-01-05
> **hugmenot said:**
> Do you have the correct apt source line? And did you update the apt-cache?
```
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts
```or ```
deb-src http://www.elisanet.fi/mlind/ubuntu edgy experimental
```

BTW, **Cairo 1.2.6** just arrived on my Feisty machine...

I try now with experimental, it seems to work. But i dont know yet, it said this

$sudo aptitude update
>updatinf lots of things..
$sudo apt-get build-dep libfreetype6 libcairo2 libxft2

The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev build-essential debhelper diffstat
  docbook docbook-to-man dpatch dpkg-dev g++ g++-4.1 gawk html2text libc6-dev
  libdirectfb-dev libdirectfb-extra libexpat1-dev libfontconfig1-dev
  libfreetype6-dev libice-dev libjpeg62-dev libpng12-dev libsm-dev libsp1c2
  libstdc++6-4.1-dev libtool libx11-dev libxau-dev libxdmcp-dev libxext-dev
  libxrender-dev libxt-dev linux-libc-dev m4 quilt sp x-dev x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev x11proto-render-dev x11proto-xext-dev
  xtrans-dev zlib1g-dev


wow... oke. install it. hope that works. but how does it find the Patch with $sudo apt-get build-dep libfreetype6 libcairo2 libxft2 ?  and not a other unpatched version from some other repostery??

---

### Post by ptr^v on 2007-01-05
i installed it, restarted x, and i see zero difference..

this is how fonts look here now, after installing windows fonts and some config files to /etc/fonts .. and installing subpixel improvements, but i dont think it worked:  [http://img479.imageshack.us/img479/4797/screenshotle8.png](http://img479.imageshack.us/img479/4797/screenshotle8.png)

but this is how i want  it:  [http://david.freetype.org/lcd/lcd-filter-1.png](http://david.freetype.org/lcd/lcd-filter-1.png)

any suggestion?

---

### Post by hugmenot on 2007-01-05
Yes, open the rosvall's tar and install all the contained debs.
To build the packages more steps a re required, all of which rosvall did for you, so to speak.

---

### Post by ptr^v on 2007-01-05
> **hugmenot said:**
> Yes, open the rosvall's tar and install all the contained debs.
To build the packages more steps a re required, all of which rosvall did for you, so to speak.
 maybe someone can tell those steps that will be great, since else i installed all this other software for nothing...

---

### Post by hugmenot on 2007-01-05
It's all in this thread.

---

### Post by ptr^v on 2007-01-06
> **hugmenot said:**
> It's all in this thread.

I have read through it..again. 

You mean this command: 

dpkg-reconfigure fontconfig-config

It changes nothing here.  

These packages contain many files:

[http://img355.imageshack.us/img355/788/screenshotck4.png](http://img355.imageshack.us/img355/788/screenshotck4.png)

I dont know what is the patch and what not or how to patch it..

Someone can clearly explain this please?

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
> 
Someone can clearly explain this please?

Perhaps I should have been more verbose. I explained how to build these packages to Ruth recently here:
[http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202](http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202)

And don&#8217;t forget that you to install the resulting debs afterwards (with dpkg -i). Only then will you have everything in place.

Report back with your progress.

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
> 
Someone can clearly explain this please?

Perhaps I should have been more verbose. I explained how to build these packages to Ruth recently here:
[http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202](http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202)

And don&#8217;t forget that you have to install the resulting debs afterwards (with dpkg -i). Only then will you have everything in place.

Also don&#8217;t forget to set subpixel rendering according to the steps in the first post.

Report back with your progress.

---

### Post by ptr^v on 2007-01-06
> **hugmenot said:**
> Perhaps I should have been more verbose. I explained how to build these packages to Ruth recently here:
[http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202](http://www.ubuntuforums.org/showpost.php?p=1903990&postcount=202)

And don’t forget that you have to install the resulting debs afterwards (with dpkg -i). Only then will you have everything in place.

Also don’t forget to set subpixel rendering according to the steps in the first post.

Report back with your progress.

thanks.. the built fails, with the --install option (same error when going to the dir manualy). so i now try to install the downloaded packages with dpkg -i , but im still not 100% sure which ones to install and which not. this is the output of the failed built:

e-definition -fno-strict-aliasing -g -O2 -MT cairo-ft-font.lo -MD -MP -MF .deps/cairo-ft-font.Tpo -c /home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c  -fPIC -DPIC -o .libs/cairo-ft-font.o
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:56:10: error: #include expects "FILENAME" or <FILENAME>
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c: In function '_render_glyph_outline':
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1169: warning: enumeration value 'FT_RENDER_MODE_NORMAL' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1169: warning: enumeration value 'FT_RENDER_MODE_LIGHT' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1169: warning: enumeration value 'FT_RENDER_MODE_MAX' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1191: warning: enumeration value 'FT_RENDER_MODE_NORMAL' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1191: warning: enumeration value 'FT_RENDER_MODE_LIGHT' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1191: warning: enumeration value 'FT_RENDER_MODE_MONO' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1191: warning: enumeration value 'FT_RENDER_MODE_MAX' not handled in switch
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1213: error: implicit declaration of function 'FT_Library_SetLcdFilter'
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1213: warning: nested extern declaration of 'FT_Library_SetLcdFilter'
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1213: error: 'FT_LCD_FILTER_DEFAULT' undeclared (first use in this function)
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1213: error: (Each undeclared identifier is reported only once
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1213: error: for each function it appears in.)
/home/peter/Desktop/tmp/libcairo-1.2.4/src/cairo-ft-font.c:1217: error: 'FT_LCD_FILTER_NONE' undeclared (first use in this function)
make[4]: *** [cairo-ft-font.lo] Error 1
make[4]: Leaving directory `/home/peter/Desktop/tmp/libcairo-1.2.4/debian/build-main/src'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/peter/Desktop/tmp/libcairo-1.2.4/debian/build-main/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/peter/Desktop/tmp/libcairo-1.2.4/debian/build-main'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/peter/Desktop/tmp/libcairo-1.2.4/debian/build-main'
make: *** [build-main-stamp] Error 2
Build command 'cd libcairo-1.2.4 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

---

### Post by ptr^v on 2007-01-06
the packages seemed to have worked, but only on firefox. Firefox looks great now, but all the rest didnt change:

[http://img465.imageshack.us/img465/8553/scrnsk5.png](http://img465.imageshack.us/img465/8553/scrnsk5.png)

I installed all .deb's. Any idea why it didnt change the rest?

---

### Post by GQed76 on 2007-01-06
```
$ gpg --recv-keys 937215FF
gpg: requesting key 937215FF from hkp server subkeys.pgp.net

```

and nothing happens

---

### Post by mlind on 2007-01-06
> **ptr^v said:**
> thanks.. the built fails, with the --install option (same error when going to the dir manualy). so i now try to install the downloaded packages with dpkg -i , but im still not 100% sure which ones to install and which not. this is the output of the failed built:


If you're building libcairo2 from experimental, you need to build it against libfreetype6 from experimental.

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
> I installed all .deb's. Any idea why it didnt change the rest?

Perhaps because you didn&#8217;t restart all the other apps?
Nautilus is running all the time. Log out and back in to see whether it worked.

---

### Post by ptr^v on 2007-01-06
> 
Perhaps because you didn&#8217;t restart all the other apps?
Nautilus is running all the time. Log out and back in to see whether it worked.



No, I logged out and back in, and restarted X, and rebooted pc, it only changed firefox. I have these settings in gnome-fonts:

[http://img378.imageshack.us/img378/3484/screenshotnw6.png](http://img378.imageshack.us/img378/3484/screenshotnw6.png) , and i installed the windows config files in /etc/fonts

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
> No, I logged out and back in, and restarted X, and rebooted pc, it only changed firefox. I have these settings in gnome-fonts:


Alright, first do "sudo dpkg-reconfigure fontconfig-config", then look whether you have a hidden ".fonts.conf" file in your home directory. It looks like something is forcing your fonts to monochrome. An earlier (forgotten) customization?

---

### Post by ptr^v on 2007-01-06
> Alright, first do "sudo dpkg-reconfigure fontconfig-config", then look whether you have a hidden ".fonts.conf" file in your home directory. It looks like something is forcing your fonts to monochrome. An earlier (forgotten) customization?

I did  "sudo dpkg-reconfigure fontconfig-config" a couple of times.. there was a .fonts.conf and .fonts.conf cache, i deleted both. This did not help. What i did was first installing the windows fonts, and after that i copied the files contained in fontconfig.tbz to /etc/fonts .  Do you use windows fonts? if yes can you maybe zip the configure files and upload it here? I dont know how many configure files there are for fonts. Does firefox use cairo just like gtk?

---

### Post by mlind on 2007-01-06
I uploaded initial packages for feisty, module is again called **fonts**. I'll upload experimental packages soon too.
```

deb http://www.elisanet.fi/mlind/ubuntu feisty fonts
deb-src http://www.elisanet.fi/mlind/ubuntu feisty fonts

```
and
```

deb http://www.elisanet.fi/mlind/ubuntu feisty experimental
deb-src http://www.elisanet.fi/mlind/ubuntu feisty experimental

```

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
>  and after that i copied the files contained in fontconfig.tbz to /etc/fonts .

I see. You could revert to the default files by reinstalling the fontconfig-config package. To use windows fonts (like Trebuchet) you do not need to futz around with system config.

Something like this should suffice:
sudo apt-get install --reinstall fontconfig-config 

[QUOTE=mlind]I uploaded initial packages for feisty, module is again called fonts. I'll upload experimental packages soon too.[/QUOTE]

Great! Thanks for your attentive work, mlind.

---

### Post by ptr^v on 2007-01-06
> **hugmenot said:**
> I see. You could revert to the default files by reinstalling the fontconfig-config package. To use windows fonts (like Trebuchet) you do not need to futz around with system config.

Something like this should suffice:
sudo apt-get install --reinstall fontconfig-config 


that changed nothing, still windows fonts as default, which is good.. i like it.  the config files from fontconfig.tbz i used are from this topic:

[http://www.ubuntuforums.org/showthread.php?t=208396&highlight=windows+fonts](http://www.ubuntuforums.org/showthread.php?t=208396&highlight=windows+fonts)

I installed the packages like this:


$ ls *.deb
freetype2-demos_2.2.1-5_amd64.deb
libcairo2_1.2.4-1ubuntu2_amd64.deb
libcairo2-dev_1.2.4-1ubuntu2_amd64.deb
libcairo2-doc_1.2.4-1ubuntu2_all.deb
libcairo-directfb2_1.2.4-1ubuntu2_amd64.deb
libcairo-directfb2-dev_1.2.4-1ubuntu2_amd64.deb
libfreetype6_2.2.1-5_amd64.deb
libfreetype6-dev_2.2.1-5_amd64.deb
libxft2_2.1.10-1ubuntu1_amd64.deb
libxft2-dbg_2.1.10-1ubuntu1_amd64.deb
libxft-dev_2.1.10-1ubuntu1_amd64.deb


$sudo dpkg -i *.deb

...



Does firefox use cairo like Gtk, or does firefox use Xft ? i seem to remember xft? the config files i copied to /etc/fonts i attached it to this msg, renamed to .zip

---

### Post by hugmenot on 2007-01-06
> **ptr^v said:**
> that changed nothing, still windows fonts as default, which is good.. i like it.  
So what&#8217;s the problem? Do you like it, or do you want to change it?

 Anyway, the only way to get the apperance we&#8217;re talking about here is to clear out all those files and replace them with the standard config files.

But beware that you might not like it if you prefer monochrome.

---

### Post by ptr^v on 2007-01-07
> **hugmenot said:**
> So what’s the problem? Do you like it, or do you want to change it?

 Anyway, the only way to get the apperance we’re talking about here is to clear out all those files and replace them with the standard config files.

But beware that you might not like it if you prefer monochrome.


I want this improved subpixel to work for the entire desktop, not only firefox. I did remove the etc/fonts files, and fonts.conf. But that still results in firefox anti-aliased, and all the other applications not. ANy other idea how to solve this problem?

---

### Post by konungursvia on 2007-01-09
> **hugmenot said:**
> First of all, the Cairo patch is for the version that is in Dapper, i.e., 1.0.4.
That’s why I said we’re waiting for 1.2.4. 
If you want to try it out you’ll have to get the sources of the affected packages, apply the patch, and rebuild plus install the result.
I really don’t have enough time to walk you through all of that right now [-( .

That's why I installed Dapper even though I only installed Ubuntu 2 weeks ago. Why use the latest software available? The second-latest is almost always far better.

---

### Post by PhineasC on 2007-01-10
The previously posted AMD64 packages do not appear to work for me either.

I can detect no discernible change after installing the packages.

I was able to get the rendering tweaks working fine on my x86 laptop using the repository.

There is a tremendous improvement.

I also tried compiling AMD64 packages myself but when I installed the DEBs no changes were visible.

---

### Post by mlind on 2007-01-10
> **PhineasC said:**
> The previously posted AMD64 packages do not appear to work for me either.

I can detect no discernible change after installing the packages.

I was able to get the rendering tweaks working fine on my x86 laptop using the repository.

There is a tremendous improvement.

I also tried compiling AMD64 packages myself but when I installed the DEBs no changes were visible.

If you have amd64 system in hand, I can walk you through the process if you wish.

---

### Post by Knorhaen on 2007-01-12
Thank you for posting this, font rendering on my new LCD is much better now.

---

### Post by hugmenot on 2007-01-12
The new performance-tuned Cairo 1.3 came to Feisty today. It still builds fine with the Turner-patch.

---

### Post by Kateikyoushi on 2007-01-12
Thanks for the guide and the repo, it did wonders to FF and I hope to seamonkey as well, now it looks as good as opera.

---

### Post by mlind on 2007-01-12
> **hugmenot said:**
> The new performance-tuned Cairo 1.3 came to Feisty today. It still builds fine with the Turner-patch.

thanks for the heads up!

---

### Post by dcstar on 2007-01-13
> **Kateikyoushi said:**
> Thanks for the guide and the repo, it did wonders to FF and I hope to seamonkey as well, now it looks as good as opera.

I have to admit that my 6.10 system looks much nicer with the basic changes, good work again!

---

### Post by mlind on 2007-01-21
freetype 2.3.0 has been promoted to stable release and it's available for download from Freetype project's website.
changelog: [https://sourceforge.net/project/shownotes.php?release_id=479191&group_id=3157](https://sourceforge.net/project/shownotes.php?release_id=479191&group_id=3157)

I'm eager to test how this affects font quality with turner patches. I'll upload new freetype and patched libcairo2 and libxft2 soon.

---

### Post by hugmenot on 2007-01-21
Sure, go ahead, but I think that since we used to build from CVS regularly 2.3.0 is just a label; not much has changed since.

EDIT: while at it, what do you think about deprecating the fonts section and promoting experimental to it? I guess Dapper needs to stay as it is because of deps, but for Edgy and Feisty the newer +/-/- patches are consistently better, right?

---

### Post by mlind on 2007-01-21
> **hugmenot said:**
> Sure, go ahead, but I think that since we used to build from CVS regularly 2.3.0 is just a label; not much has changed since.

EDIT: while at it, what do you think about deprecating the fonts section and promoting experimental to it? I guess Dapper needs to stay as it is because of deps, but for Edgy and Feisty the newer +/-/- patches are consistently better, right?

Yes, I'll try to do the deprecation thingy  tomorrow and post back. One thing I haven't been able to figure out is why default Ubuntu fonts look bigger with newer freetype. Any ideas?
I should also probably tighten the dependencies of libxft2 and libcairo2 for libfreetype6 at least at build time.

/edit
font size issue doesn't seem to be problem when using **Native** hinting mode and result looks good.

---

### Post by mlind on 2007-01-21
I also posted this on the Feisty forums: [http://www.ubuntuforums.org/showthread.php?t=343670](http://www.ubuntuforums.org/showthread.php?t=343670)

---

### Post by mata_svada on 2007-01-22
I was wondering which exact patches you are applying to freetype (no patches needed here since 2.3.0, just enabling the option, right?), cairo and libxft because I'm trying to get the same great ClearType rendered fonts on Arch Linux.

Do any default Debain-patches affect Subpixel rendering?

---

### Post by mlind on 2007-01-22
> **mata_svada said:**
> I was wondering which exact patches you are applying to freetype (no patches needed here since 2.3.0, just enabling the option, right?), cairo and libxft because I'm trying to get the same great ClearType rendered fonts on Arch Linux.

Do any default Debain-patches affect Subpixel rendering?

You can find the patches on the first post of this thread. You have to export **FT_CONFIG_OPTION_SUBPIXEL_RENDERING** which you probably meant by *enabling the option*. There are some Debian-specific patches in the freetype package I'm building, but you'll find these out by downloading the source package. TT_CONFIG_OPTION_BYTECODE_INTERPRETER seems to be enabled as well.

You'll also need to patch libcairo2 and libxft2 with Turner's patches, depending on which freetype version you're using.
I'm not sure if fontconfig needs to be patched in Arch, it's not required in Ubuntu.

---

### Post by mata_svada on 2007-01-31
Thanks for your help. I managed to get really good fonts when running Arch Linux using the turner patch and enabling TT_CONFIG_OPTION_BYTECODE_INTERPRETER.

But there are still problems with bold fonts. They are blurry and occationally they are duper-bold. Do you know whether there is a patch or an option that could solve that issue?

---

### Post by mlind on 2007-02-05
> **mata_svada said:**
> Thanks for your help. I managed to get really good fonts when running Arch Linux using the turner patch and enabling TT_CONFIG_OPTION_BYTECODE_INTERPRETER.

But there are still problems with bold fonts. They are blurry and occationally they are duper-bold. Do you know whether there is a patch or an option that could solve that issue?

I think you're facing the super-bolding issue which happens on certain font settings. Take a look at hugmenot's first post on this thread about using local **fonts.conf** to reduce bolding.

---

### Post by desperado666 on 2007-02-19
where are the packages??? Cant download them from the repository.

---

### Post by desperado666 on 2007-02-19
..

---

### Post by Joe_Bishop on 2007-02-19
man source.list

---

### Post by desperado666 on 2007-02-19
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# deb [http://malteo.homelinux.net](http://malteo.homelinux.net) edgy-malteo all #murrine
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy 3v1n0
# deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main
# deb [http://dvdstyler.sourceforge.net/repository/ubuntu/](http://dvdstyler.sourceforge.net/repository/ubuntu/) dapper testing
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy main
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy experimental
# deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

---

### Post by mundano on 2007-02-20
Is any way to install this packages in feisty?

---

### Post by mlind on 2007-02-20
> **mundano said:**
> Is any way to install this packages in feisty?

[http://www.ubuntuforums.org/showthread.php?t=343670](http://www.ubuntuforums.org/showthread.php?t=343670)

---

### Post by SuSUntu on 2007-02-21
Do the patched files need to be "pinned" to prevent overwriting when official packages are updated? Basically, I'd like some insight into how the apt update process works for these types of "patched" files.

Sorry if this has been asked, but I read through the entire thread yesterday prior to updating my files (I tried both sets and ended up using the edgy experimental files), but my focus was not on the update issue I'm asking about here, so I could have skimmed over an answer without retaining the information ... and I just don't have the willpower to read through it all again. :)

Thank you.

---

### Post by mlind on 2007-02-21
> **SuSUntu said:**
> Do the patched files need to be "pinned" to prevent overwriting when official packages are updated? Basically, I'd like some insight into how the apt update process works for these types of "patched" files.

Sorry if this has been asked, but I read through the entire thread yesterday prior to updating my files (I tried both sets and ended up using the edgy experimental files), but my focus was not on the update issue I'm asking about here, so I could have skimmed over an answer without retaining the information ... and I just don't have the willpower to read through it all again. :)

Thank you.

Yes, pinning would be necessary. I'm not sure if it's a good idea from me to use versioning where every Ubuntu update will be considered newer than my patched library. I guess the idea was that I would notice the downstream update immediately and update my custom packages right away. So patched libs are updated if Ubuntu releases version with higher version number unless you use pinning.

dpkg and APT package handling utilities are clever. They allow you to safely upgrade, downgrade and pin these packages. These patched libs perform no differently in this area than any other .deb packages. I often use pinning (see *man apt_preferences*) and usually downgrade packages using aptitude.

Good thing is that core libraries like libfreetype6, libcairo2 and libxft2 should only get security updates and usually it means very seldom if at all. For Dapper I guess there's been only one security update for these files so far.

---

### Post by SuSUntu on 2007-02-22
> **mlind said:**
> Yes, pinning would be necessary. I'm not sure if it's a good idea from me to use versioning where every Ubuntu update will be considered newer than my patched library. I guess the idea was that I would notice the downstream update immediately and update my custom packages right away. So patched libs are updated if Ubuntu releases version with higher version number unless you use pinning.


This was the way I hoped it worked. I prefer to have the options to retain the updates via pinning or to allow the official updates to be installed in place of the patched files. The alternative possibility of having relevant updates ignored completely as a result of installing these packages was my real concern. 

Thank you very much for the reply.

---

### Post by mlind on 2007-02-22
> **SuSUntu said:**
> This was the way I hoped it worked. I prefer to have the options to retain the updates via pinning or to allow the official updates to be installed in place of the patched files. The alternative possibility of having relevant updates ignored completely as a result of installing these packages was my real concern. 

Thank you very much for the reply.

There's a problem with this setup though. 3 libraries should have tighter dependencies with each other or at least with patched libfreetype6. If Ubuntu releases update for freetype, fonts may become very ugly because other patched libs are missing this shared patched library. Although I don't know a thing about the internals of these libraries and it could be that necessary bits are required only at build time.

Anyway, I'm thinking of adding strict dependencies between these three libs. If one is missing, other two are in broken state.

---

### Post by hugmenot on 2007-02-22
> **mlind said:**
> Anyway, I'm thinking of adding strict dependencies between these three libs. If one is missing, other two are in broken state.

I&#8217;m all for it. There&#8217;s no other way to tell with which flags the three libs have been compiled.

---

### Post by BulletzBill on 2007-02-24
I just installed the font rendering packages provided on the first post of this thread, however it does not seem like it did anything, or at least it does not look improved.

Here is what text in firefox looks like now after I installed the packages (I did logout and reboot):
[IMG]http://1updesign.net/misc/fonts.jpg[/IMG]

In my system Font Preferences I am using all Sans with Subpixel smoothing, 96dpi, Full Hinting, RGB Subpixel order. And in Firefox my default font is sans-serif.

My regular application and desktop fonts (menus, toolbars, ect.) have always looked pretty good, it was just the font rendering in Firefox I wanted to improve, as it is really very inferior to the font rendering under Windows.

If anyone has any ideas on what I may have done wrong, I would greatly appreciate hearing them. Thanks.

---

### Post by hugmenot on 2007-02-24
> **BulletzBill said:**
> If anyone has any ideas on what I may have done wrong, I would greatly appreciate hearing them. Thanks.

Your screenshot is very strange. There&#8217;s clearly some filtering going on but it is very faint. The filtering definitely comes from our packages because the stems are not fitted (i.e., you can see lateral colors).
You also do not seem to have some freaky gamma correction in your XServer because the rest of the page looks okay.

Is there anything else special that can explain this?

[in the screenshot the lower left overlay shows how it should be]

---

### Post by BulletzBill on 2007-02-24
Thanks for the response, but no I can't think of anything else that I am doing that would explain it. I am actually very new to Ubuntu, just installed it a few days ago, I have everything at pretty much the default settings except for installing these packages, so I really have no idea what could be causing it to look like that.

---

### Post by BulletzBill on 2007-02-25
By the way, how can I revert to the default font rendering packages that came installed?  And also revert back to the original settings in the .conf files in /etc/fonts? I just want to try and compare what it originally looked like before to see if maybe something was screwed up to begin with.

Thanks

---

### Post by buttons on 2007-02-26
> **BulletzBill said:**
> I just installed the font rendering packages provided on the first post of this thread, however it does not seem like it did anything, or at least it does not look improved.

Here is what text in firefox looks like now after I installed the packages (I did logout and reboot):
[IMG]http://1updesign.net/misc/fonts.jpg[/IMG]

In my system Font Preferences I am using all Sans with Subpixel smoothing, 96dpi, Full Hinting, RGB Subpixel order. And in Firefox my default font is sans-serif.

My regular application and desktop fonts (menus, toolbars, ect.) have always looked pretty good, it was just the font rendering in Firefox I wanted to improve, as it is really very inferior to the font rendering under Windows.

If anyone has any ideas on what I may have done wrong, I would greatly appreciate hearing them. Thanks.

I have the same issue.  I had this working last week before I completely hosed my system (lax ext3 crash recovery settings and playing around with experimental kernel patchsets don't mix well).  Prior to this, everything was beautiful, and now nothing seems to work.  The oddest part is things like .fonts.conf appear to have absolutely no effect.

The only thing I can think of is perhaps one or more of the three patched libraries (libxft2, libfreetype6, libcairo2) isn't being pulled from mlind's repo but rather ubuntu's.  When I added the repo (both font and experimental) to my sources only xft2 and freetype were updated.

I'm at work now so I can't check to see if this is the case.

Also, firefox is even worse than the rest of the system, enabling in about:config fonts.autohinted true fonts.unhinted false and font.freetype2 true helps a bit, although I'm bothered by the fact that I didn't have to do this before and having just read this entire thread it seems no one else does, either.  I guess I'll try pango when I get home.

ideas?  I miss stunning fonts.

---

### Post by buttons on 2007-02-26
Could someone post an apt-get line that installs the specific versions from the repo rather than ubuntus?  I'll pin them after that.

Thanks much

---

### Post by 3zero2 on 2007-02-27
so i was thinking that the patches weren't wokrking anymore so i checked the thread to see if someone else has the same problem.

it comes out that synaptic decided to install ubuntu's libcairo2 1.2.4-1ubuntu2.2. i can see the 1.2.4-1ubuntu2+turner1e but it is not installed. Same thing goes for libxft.

libfreetype6 is 2.3.1-0mlind1~edgy1.

is there any way to fix this?

---

### Post by mlind on 2007-02-27
> **3zero2 said:**
> so i was thinking that the patches weren't wokrking anymore so i checked the thread to see if someone else has the same problem.

it comes out that synaptic decided to install ubuntu's libcairo2 1.2.4-1ubuntu2.2. i can see the 1.2.4-1ubuntu2+turner1e but it is not installed. Same thing goes for libxft.

libfreetype6 is 2.3.1-0mlind1~edgy1.

is there any way to fix this?

yeah, I screwed up some time ago with the repository, sorry about that. experimental packages were promoted to fonts module and packages in fonts are now gone. You can see exact versions using **apt-cache madison**
but here they are anyway.
```

sudo aptitude install libfreetype6=2.3.1-0mlind1~edgy1 libcairo2=1.2.4-1ubuntu2+turner1e libxft2=2.1.10-1ubuntu1+turner1e 

```

---

### Post by buttons on 2007-02-27
Even with the correct packages I'm still getting awful coloured pixels on anything slanted, such as Ws and italics.

Any suggestions?

---

### Post by mlind on 2007-02-28
> **buttons said:**
> Even with the correct packages I'm still getting awful coloured pixels on anything slanted, such as Ws and italics.

Any suggestions?

I'll take a look of this later. btw did you run dpkg-reconfigure fontconfig after installing the packages? Try removing custom fonts.conf if you have one.

---

### Post by buttons on 2007-02-28
Yes and yes.  Neither appeared to do anything :-|

---

### Post by hugmenot on 2007-02-28
> **buttons said:**
> Even with the correct packages I'm still getting awful coloured pixels on anything slanted, such as Ws and italics.

The color fringing shouldn&#8217;t be awful. Barely noticeable at normal viewing distance would be better.
Are you positive that you also have the Cairo and Xft from the repo? Otherwise you would see double strength filtering.

---

### Post by buttons on 2007-02-28
> **hugmenot said:**
> The color fringing shouldn’t be awful. Barely noticeable at normal viewing distance would be better.
Are you positive that you also have the Cairo and Xft from the repo? Otherwise you would see double strength filtering.

I would love to see that!  Italics are especially colourful.  If I zoom in, I can see that the entire text is virtually nothing but colour and the only "black" is in my head.

I have downgraded the packages, and then reinstalled everything per the command:

sudo aptitude install libfreetype6=2.3.1-0mlind1~edgy1 libcairo2=1.2.4-1ubuntu2+turner1e libxft2=2.1.10-1ubuntu1+turner1e

removed my .fonts.conf and did a dpkg-reconfigure.

I have Native, Automatic, and said NO to bitmapped fonts.

My fonts in gnome are subpixel with full hinting.  Slight hinting is interesting, it kinda blurs the text which makes the colours less noticeable.  Medium and Full are both ridiculous.  RGB, of course, which I actually looked up for my monitor just to make sure.

I'm stumped.  Between this and weird "half" regression of opengl performance (like 15 fps off all games) I've seemingly managed to screw up my new installation without doing anything different that I can see.

Any help is appreciated.

---

### Post by fotakis on 2007-02-28
I think the repo is down?

---

### Post by suRoot on 2007-02-28
> **fotakis said:**
> I think the repo is down?

yep, having problems too!

---

### Post by mlind on 2007-02-28
> **fotakis said:**
> I think the repo is down?

it should be working. I had to remove the experimental module, so use **fonts** from now on.

---

### Post by hugmenot on 2007-02-28
> **mlind said:**
> it should be working. I had to remove the experimental module, so use **fonts** from now on.

Updated first post to reflect this change. There&#8217;s no more original Turner -/+/+ style packages, right?

---

### Post by mlind on 2007-03-02
> **hugmenot said:**
> Updated first post to reflect this change. There’s no more original Turner -/+/+ style packages, right?

currently no. I can put those back again if someone needs them though.

---

### Post by Mustard007 on 2007-03-02
Where I can find package for Feisty ?

Thanks...

---

### Post by mlind on 2007-03-03
> **Mustard007 said:**
> Where I can find package for Feisty ?

Thanks...

[http://www.ubuntuforums.org/showthread.php?t=343670](http://www.ubuntuforums.org/showthread.php?t=343670)

---

### Post by Mustard007 on 2007-03-03
This links doesn't work anymore ! Try yourself...

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty fonts

If you have the .deb with you, can you send somewhere...?

Thanks you !!

---

### Post by mlind on 2007-03-05
> **Mustard007 said:**
> This links doesn't work anymore ! Try yourself...

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty fonts

If you have the .deb with you, can you send somewhere...?

Thanks you !!

it works okay, but repository is not browseable/indexed. Just copy&paste repository locations to your sources.list and upgrade

```

$ apt-cache madison libcairo2
libcairo2 | 1.3.14-0ubuntu1+turner1e | http://www.elisanet.fi feisty/fonts Packages

```

---

### Post by skip27 on 2007-03-05
I just installed the packages under Edgy and I like it very much! I think this thread deserves a sticky. I'll go so far as to say that the rendering surpasses that of Windows. Great job.

---

### Post by Quicksand on 2007-03-05
WOW what a difference!  Font rendering had been my primary complaint with Ubuntu compared to Windows.  Now it's stunningly beautiful, and with hinting set to "Slight," I think it looks even better than Windows.

Is there a repository with 64-bit packages for Edgy yet?  I grabbed the patched source (from [http://ubuntu.moshen.de/dists/feisty/experimental/](http://ubuntu.moshen.de/dists/feisty/experimental/)) and built the .deb files myself last night because I couldn't find them anywhere.  I'd be happy to provide them if someone is interested in hosting.

Just let me know what files you need.

---

### Post by mlind on 2007-03-05
> **Quicksand said:**
> WOW what a difference!  Font rendering had been my primary complaint with Ubuntu compared to Windows.  Now it's stunningly beautiful, and with hinting set to "Slight," I think it looks even better than Windows.

Is there a repository with 64-bit packages for Edgy yet?  I grabbed the patched source (from [http://ubuntu.moshen.de/dists/feisty/experimental/](http://ubuntu.moshen.de/dists/feisty/experimental/)) and built the .deb files myself last night because I couldn't find them anywhere.  I'd be happy to provide them if someone is interested in hosting.

Just let me know what files you need.

It would be great if you'd like to provide amd64 packages for Edgy. Could you grab the source packages from edgy's **fonts** repository and build those instead (make sure you build packages against patched libfreetype6).

source repository is
```

deb-src http://www.elisanet.fi/mlind/ubuntu edgy fonts

```

---

### Post by Quicksand on 2007-03-06
Okay, I grabbed the sources from elisanet.fi and built the following:

[LIST]
[*]freetype2-demos_2.3.1-0mlind1~edgy1_amd64.deb
[*]libcairo2_1.2.4-1ubuntu2+turner1e_amd64.deb
[*]libcairo2-dev_1.2.4-1ubuntu2+turner1e_amd64.deb
[*]libcairo2-doc_1.2.4-1ubuntu2+turner1e_all.deb
[*]libcairo-directfb2_1.2.4-1ubuntu2+turner1e_amd64.deb
[*]libcairo-directfb2-dev_1.2.4-1ubuntu2+turner1e_amd64.deb
[*]libfreetype6_2.3.1-0mlind1~edgy1_amd64.deb
[*]libfreetype6-dev_2.3.1-0mlind1~edgy1_amd64.deb
[*]libxft2_2.1.10-1ubuntu1+turner1e_amd64.deb
[*]libxft2-dbg_2.1.10-1ubuntu1+turner1e_amd64.deb
[*]libxft-dev_2.1.10-1ubuntu1+turner1e_amd64.deb
[/LIST]
I installed them and everything is working great.

Where do you want 'em? :mrgreen: 

(I'm such a newbie I had to learn how to get sources from a repository and build them into .deb files -- the other ones I had downloaded manually.  Heh.  I'm glad it's easy and I'm not stuck here scratching my head!)

---

### Post by Mustard007 on 2007-03-06
Thanks mlind !!!
;)

---

### Post by llamakc on 2007-03-09
Thanks mlind. I hope the repository is back up soon. I made a mistake and lost my better fonts!

EDIT: I didn't catch the change for the sources.list line. Finally figured it out.

---

### Post by phelge on 2007-03-12
Hello,

Following user Hugmenot advice I'm posting this to share my experience. First I'm totally new to Ubuntu and not at all a font expert. Usually I rather use rpm based distros (pclinuxos, mandriva), with which the D. Turner patches work wery well and give very nice looking fonts (usually MS fonts) by following [http://jaganath.wordpress.com/2006/11/16/cleartype-lcd-patch-on-mandriva-linux-2007/](http://jaganath.wordpress.com/2006/11/16/cleartype-lcd-patch-on-mandriva-linux-2007/).

With Ubuntu I applied the patched cairo, Xft, freetype debs of user mlind, and I'm quite disappointed compared with what I had with other distros. See attached screenshot mlind-debs.

So I downloaded the 3 sources cairo, Xft and freetype-2.2.1 and recompiled everything following the previous howto, and then I got much better (at least for me) font rendering. See attached screenshot source-compiled.

It seems the difference is that I use freetype-2.2.1 and mlind uses freetype-2.3.2 which may have different default algorithms. I wonder if there is a way to configure freetype-2.3.2 to get the same result as with 2.2.1. User Hugmenot told that there is not one but 3 different algorithms (default, legacy, light) and legacy seems to correspond to what I get with self compiled libs.

Thanks for your help

PS : In the screenshots the menu font is segoe and the mozilla font is Trebuchet MS
PS2 : I tried to download the deb source package freetype-2.3.2 and I got some MD5SUM errors.

---

### Post by mlind on 2007-03-12
oops, thanks for pointing out the MD5sum error..
You might want to check out freetype documentation if you want to experiment with different hinting algorithms.

---

### Post by hugmenot on 2007-03-12
> **phelge said:**
> 
PS : In the screenshots the menu font is segoe and the mozilla font is Trebuchet MS


Hello phelge,
the screenshots are good, but you forgot to mention which image shows which settings.
Please also state which hinting method you use (i.e. autohinter vs. BCI and slight, medium or full).

In the thread that I referred you to Xft and Cairo developers utter their doubts about David&#8217;s newer filter method. He explains [here]("http://article.gmane.org/gmane.comp.lib.cairo/9347") how the different options can be toggled during compilation (in ftoption.h) and how he gets superior results for autohinting and consistent results across all hinting modes. The patches that are used in the howto you link to really correspond to the legacy method, only that the filtering is done inside Freetype and not by Cairo of Xft.

---

### Post by SuSUntu on 2007-03-13
Just got the updates to the packages via the Update Manager:

Upgraded the following packages:
libcairo2 (1.2.4-1ubuntu2+turner1e) to 1.2.4-1ubuntu2+turner2
libcairo2-dev (1.2.4-1ubuntu2+turner1e) to 1.2.4-1ubuntu2+turner2
libfreetype6 (2.3.1-0mlind1~edgy1) to 2.3.2-0mlind1~edgy1
libfreetype6-dev (2.3.1-0mlind1~edgy1) to 2.3.2-0mlind1~edgy1
libxft-dev (2.1.10-1ubuntu1+turner1e) to 2.1.10-1ubuntu1+turner2
libxft2 (2.1.10-1ubuntu1+turner1e) to 2.1.10-1ubuntu1+turner2


Thanks.

---

### Post by phelge on 2007-03-13
Hello hugmenot,

Using the mlind packages, I had bad results with Native. The screenshot is with Autohinter, Always, No, and hinting medium

Using the source compiled libs, the same.

I played a bit with LEGACY and LIGHT by defining in ftoption.h FT_FORCE_LEGACY_LCD_FILTER or  FT_FORCE_LIGHT_LCD_FILTER.

LEGACY doesn't give good results. LIGHT is much better with full hinting and is almost equivalent to what I had with self compiled libs (see previous screenshot)

Thanks for your help

---

### Post by mlind on 2007-03-13
phelge, are you using tft/lcd panel or CRT tube ?

---

### Post by phelge on 2007-03-14
I have 15" laptop at the office and a 20" LCD screen at home.

---

### Post by EDzior on 2007-03-16
> **phelge said:**
> Hello hugmenot,

Using the mlind packages, I had bad results with Native. The screenshot is with Autohinter, Always, No, and hinting medium

Using the source compiled libs, the same.

I played a bit with LEGACY and LIGHT by defining in ftoption.h FT_FORCE_LEGACY_LCD_FILTER or  FT_FORCE_LIGHT_LCD_FILTER.

LEGACY doesn't give good results. LIGHT is much better with full hinting and is almost equivalent to what I had with self compiled libs (see previous screenshot)

Thanks for your help

Hello phelge,
did you play with LEGACY and LIGHT options using the sources from mlind repo or  original sources? i would like to try to get the same results as you shown on your source-compiled screenshot.
Regards.

---

### Post by phelge on 2007-03-17
Hello EDzior,
Finally after several tests, the DEFAULT algorithm is giving the best results for me. Concerning the the source compiled screenshot instructions see my previous post.

Using the current mlind packages, I think I have found how to have the same rendering. Here is what I did :
1 - I installed the 3 mlind binary debs : libcairo, libXft and libfreetype
2 - I downloaded the source deb of libfreetype-2.3.2
3 - In freetype-2.3.2/debian/patches-freetype I cancelled the patches enable-full-bytecode-interpreter and freetype-bytecode-interpreter.patch
4 - In src/autohint/aflatin.c I removed the OR statement in the two occurences which contain : FT_RENDER_MODE_MONO so it gives :
if ( mode == FT_RENDER_MODE_MONO )
5 - Compiled with dpkg-buildpackage -rfakeroot -us -uc
6 - sudo dpkg-reconfigure fontconfig-config : Autohint, Always, No
7 - In gnome : prefs -> fonts : subpixel and hinting FULL

I've attached the original source compiled screenshot, screenshot done with freshly compiled libfreetype packages. There is a small difference, in the later there is more space between letters.

I've attached the package if you want to try it.
Hope this helps
PS : I'm completly new to Ubuntu and Debian and forgive me if some steps should not be as I did

---

### Post by EDzior on 2007-03-17
> **phelge said:**
> 
I've attached the package if you want to try it.
Hope this helps

Thanks.
I will try this later when i will be on machine with Ubuntu.
I've tried to get better font rendering on openSUSE 10.2 with KDE (using this info [http://jaganath.wordpress.com/2006/11/16/cleartype-lcd-patch-on-mandriva-linux-2007/](http://jaganath.wordpress.com/2006/11/16/cleartype-lcd-patch-on-mandriva-linux-2007/) )
but as far as i can see the result is not that good as i wish :(

---

### Post by Megatog615 on 2007-03-22
```
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
```?
I get this when I try to register the key.

---

### Post by mlind on 2007-03-22
> **Megatog615 said:**
> ```
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
```?
I get this when I try to register the key.

try using
```

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF

```

---

### Post by Megatog615 on 2007-03-22
```
gpg: requesting key 937215FF from hkp server subkeys.pgp.net
gpg: can't open `/home/megatog615/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
```

Tried it with sudo and it worked.

---

### Post by mlind on 2007-03-22
> **Megatog615 said:**
> ```
gpg: requesting key 937215FF from hkp server subkeys.pgp.net
gpg: can't open `/home/megatog615/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0
```

Tried it with sudo and it worked.

don't use sudo because ~/.gnupg folder and files will probably get owned by root.
If this happened, you should chown modified files back to yourself.

---

### Post by tomjol on 2007-03-26
Wow, this really is spectacular! Lack of font clarity really was a bit of a stumbling block for me in my attempts to shift away from Windows, given how many hours I spend staring at a monitor, but this has just taken the whole issue and thrown it right out the window!

Huge thanks to everyone involved in developing, hosting and publicising this.

---

### Post by mlind on 2007-03-31
@hugmenot
I changed my ISP and repository addresses also changed. Could you update the main page with
```

deb http://www.telemail.fi/mlind/ubuntu edgy fonts
deb-src http://www.telemail.fi/mlind/ubuntu edgy fonts

```

Thanks.

---

### Post by hugmenot on 2007-04-01
> **mlind said:**
> @hugmenot
I changed my ISP and repository addresses also changed. Could you update the main page with
```

deb http://www.telemail.fi/mlind/ubuntu edgy fonts
deb-src http://www.telemail.fi/mlind/ubuntu edgy fonts

```

Thanks.

Done. BTW thanks for all your efforts building and hosting. Much appreciated!

---

### Post by mlind on 2007-04-01
> **hugmenot said:**
> Done. BTW thanks for all your efforts building and hosting. Much appreciated!

yeah, no problem :mrgreen:

---

### Post by Lucifiel on 2007-04-02
Hmmm I downloaded the Cairo patch for 1.0.4(that is, dapper). However, any ideas on how to install it?

Edit: It's definitely gksudo / sudo something something, right?

---

### Post by mlind on 2007-04-02
> **Lucifiel said:**
> Hmmm I downloaded the Cairo patch for 1.0.4(that is, dapper). However, any ideas on how to install it?

Edit: It's definitely gksudo / sudo something something, right?

It's somewhat more complicated process. There should be existing thread for Dapper about this same subject floating somewhere in the forums.
That thread should contain link for a repository with Dapper binaries.

---

### Post by gribelu on 2007-04-04
I just installed this on Feisty Beta1 (it's in the repo, i guess they forgot to tell us :) ) and the difference is amazing. Thanks!

---

### Post by qasd on 2007-04-07
I'm not able to select the bytecode interpreter. I can only choose betweeen native autohinter and none(see screenshot). Am I missing something? I installed the packages correctly.

---

### Post by mlind on 2007-04-07
> **qasd said:**
> I'm not able to select the bytecode interpreter. I can only choose betweeen native autohinter and none(see screenshot). Am I missing something? I installed the packages correctly.

Bytecode Interpreter is enabled by default. Option can be enabled/disabled at build time.
Freetype package is built using
```

#define TT_CONFIG_OPTION_BYTECODE_INTERPRETER

```

---

### Post by softtower on 2007-04-08
This is truly amazing. Crappy looking fonts was mostly the reason why I kept going back to Windows over the years, keeping my Linux interest strongly aligned with my server-side development needs.

This patch is what truly allows me to actually use X. Thank you!!!

---

### Post by anshuljain on 2007-04-14
Mlind...I have to bow and salute you, your packages are the single reason i've stuck to (K)Ubuntu ant not bolted to distros with far better look and feel like Fedora 7 or Mandriva 2007.1. I just installed your packages on Feisty and with the right tweaking...i've never known a desktop could look this sexy!!

---

### Post by mlind on 2007-04-14
> **anshuljain said:**
> Mlind...I have to bow and salute you, your packages are the single reason i've stuck to (K)Ubuntu ant not bolted to distros with far better look and feel like Fedora 7 or Mandriva 2007.1. I just installed your packages on Feisty and with the right tweaking...i've never known a desktop could look this sexy!!

Thank you, although you should thank Freetype team instead (especially David Turner himself) and hugmenot who brought this to my attention. I just patch and compile the packages.

It's always good to hear others are enjoying nice looking fonts nevertheless :)

---

### Post by ihavenoname on 2007-04-14
wow, that's all I can say.

---

### Post by kumar20 on 2007-04-15
worked without a hitch.
Thanks a lot

---

### Post by Freddd on 2007-04-16
I get the following message when I try to run apt-get dist-upgrade
```
===Error. The following diversions still exist:
diversion of /usr/share/man/man1/locate.1.gz to /usr/share/man/man1/locate.notslocate.1.gz by slocate
diversion of /usr/share/man/man1/updatedb.1.gz to /usr/share/man/man1/updatedb.notslocate.1.gz by slocate
===============================================
dpkg: error processing /var/cache/apt/archives/slocate_3.1-1ubuntu0.1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_3.1-1ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do to successfully install it?

---

### Post by fotakis on 2007-04-19
Hello again mlind,

I was able to install your packages but once I restarted X I couldn't get a gdm login screen, I could see the little mouse waiting handle but everything behind seemed to flicker...

Any suggestions?

Best Regards

---

### Post by mlind on 2007-04-19
> **fotakis said:**
> Hello again mlind,

I was able to install your packages but once I restarted X I couldn't get a gdm login screen, I could see the little mouse waiting handle but everything behind seemed to flicker...

Any suggestions?

Best Regards

I've never experienced such issue with Ubuntu. Does this happen if you downgrade the patched font packages to Ubuntu versions?

---

### Post by fotakis on 2007-04-20
Hello mlind,

That was the only way I was able to log back in

Best Regards

---

### Post by Randall311 on 2007-04-27
Do these patches work for Feisty as well as Edgy?

---

### Post by mlind on 2007-04-27
> **Randall311 said:**
> Do these patches work for Feisty as well as Edgy?

hiya, there's a separate thread for Feisty
[http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

---

### Post by foof on 2007-11-04
Are there packages for gutsy as well? ..and do they work for Kubuntu too?

---

### Post by sclough on 2007-11-04
If you're referring to the telemail.fi repository, it appears to have Gutsy packages.

Since these packages are for X font rendering I don't see any reason why they wouldn't work in KDE as well as Gnome unless KDE does something special with font rendering.

---

### Post by mlind on 2007-11-04
> **foof said:**
> Are there packages for gutsy as well? ..and do they work for Kubuntu too?

There are no packages for Gutsy as the patches were included in official Ubuntu packages.
[http://ubuntuforums.org/showthread.php?t=489326](http://ubuntuforums.org/showthread.php?t=489326)

---

