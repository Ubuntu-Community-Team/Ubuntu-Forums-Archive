---
title: "Improved subpixel font rendering for Feisty"
date: 2007-01-21
forum: Desktop Environments
---

### Post by mlind on 2007-01-21
For reference see **hugmenot**'s related [[COLOR="Sienna"]Edgy thread[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=235526"). There's also [a thread for Gutsy]("http://ubuntuforums.org/showthread.php?t=489326") users.

Patched libraries are built against **freetype** 2.3.x (not currently in feisty) and include [COLOR="Blue"]David Turner[/COLOR]'s subpixel rendering [patches]("http://david.freetype.org/lcd/").
```

deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

```
**[COLOR="Blue"][edit][/COLOR]**
for **amd64** binaries use [RAOF's repository]("http://ubuntu.moshen.de/dists/feisty/experimental")
```

deb http://raof.dyndns.org/falcon feisty experimental
deb-src http://raof.dyndns.org/falcon feisty experimental

```

[COLOR="Silver"]Alternative repository, for experimental builds only.[/COLOR]
```

deb http://www.telemail.fi/mlind/ubuntu feisty experimental
deb-src http://www.telemail.fi/mlind/ubuntu feisty experimental

```


**Notes**
[LIST]
[*]To install the packages
```

sudo aptitude update
sudo aptitude install libfreetype6 libcairo2 libxft2

```
[*]After the install, you may want reconfigure font settings. I'm currently using Feisty defaults (Native, **Always**, No bitmapped fonts) myself.
```

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

```
[*]If you get errors about **missing gpg key**
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | **sudo** apt-key add -

```
(or alternatively)
```

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

```
[*]GPG key to RAOF's repository (amd64 packages)
```

wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

```
[*]If you later decide to go back to Ubuntu packages, you must downgrade **all** three installed packages
[*]You'll probably need to restart X-server after installing the packages to see the changes apply
[/LIST]

---

### Post by hugmenot on 2007-01-21
The name&#8217;s David, [news at eleven]("http://en.wikipedia.org/wiki/Ted_Turner") :roll: .

Oh, and mentioning the repo signing key can&#8217;t hurt.

---

### Post by mercurysquad on 2007-01-21
David Turner, indeed :P

Thanks for the repository, I was using my own patched debs, but I just reinstalled Herd 2 from scratch and my debs affected everything but Firefox. Your repository fixed that!

The 'older' patches are definitely better looking. That's not even subjective, because with Autohinter turned on, sites like Wikipedia have weird mono-space font like spacing between letters and words. Native hinter fixes that but the fonts themselves look like crap.

Downgrading to your feisty fonts (rather than experimental) patches fixed all such issues.

---

### Post by firephoto on 2007-01-21
Is this only for gnome or will it work with KDE also?

---

### Post by mlind on 2007-01-22
> **hugmenot said:**
> The name’s David, [news at eleven]("http://en.wikipedia.org/wiki/Ted_Turner") :roll: .

Oh, and mentioning the repo signing key can’t hurt.

:mrgreen: oops

---

### Post by hugmenot on 2007-01-22
> **mlind said:**
> :mrgreen: oops

[Considering he is a Frenchman]("http://www.advogato.org/person/freetype/") I wonder how that name sounds in french ...

BTW, I had a serious laugh looking at the link in his last post there.

---

### Post by mlind on 2007-01-22
@ firephoto
There should work with any application using freetype, libxft2 or libcairo2 I guess.

@ hugmenot
Have you tried out packages in experimental repo using
fontconfig-config:
 * Native, Automatic, No bitmapped fonts
GNOME font settings
 * Subpixel smoothing, Full hinting

I think there's been improvement since edgy with newer libfreetype6 and libcairo2.
Font's seem more clear to my eyes and there's less artifacts. Any opinions?

---

### Post by caryb on 2007-01-23
W: GPG error: [http://www.elisanet.fi](http://www.elisanet.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
root@STINKPAD:/etc/apt#          

It no worky!



Cary

---

### Post by mlind on 2007-01-23
> **caryb said:**
> W: GPG error: [http://www.elisanet.fi](http://www.elisanet.fi) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFFF5E937215FF
W: You may want to run apt-get update to correct these problems
root@STINKPAD:/etc/apt#          

It no worky!



Cary

see first post about **missing gpg key**,

---

### Post by ~LoKe on 2007-01-23
> ~$ gpg --recv-keys 937215FF gpg --export --armor 937215FF | sudo apt-key add -
gpg: "gpg" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "--armor" not a key ID: skipping
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
gpg: no valid OpenPGP data found.

What's the url for the key so I can wget it?

---

### Post by chrisoverzero on 2007-01-23
> **~LoKe said:**
> What's the url for the key so I can wget it?
Try throwing a sudo before each gpg and a && before the second one.

sudo gpg --recv-keys 937215FF && sudo gpg --export --armor 937215FF | sudo apt-key add -

The sudos may not be necessary, but they seemed to be on my machine.

---

### Post by ~LoKe on 2007-01-23
> **chrisoverzero said:**
> Try throwing a sudo before each gpg and a && before the second one.

sudo gpg --recv-keys 937215FF && sudo gpg --export --armor 937215FF | sudo apt-key add -

The sudos may not be necessary, but they seemed to be on my machine.

> $ sudo gpg --recv-keys 937215FF && sudo gpg --export --armor 937215FF | sudo apt-key add -
Password:
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
:(

---

### Post by eremini on 2007-01-23
Fonts look good in kde (sans serif), but bad in gnome (got it set to verdana). Which font/size do u recomend using?

---

### Post by hugmenot on 2007-01-23
> **mlind said:**
> @ hugmenot
Have you tried out packages in experimental repo using
fontconfig-config:
 * Native, Automatic, No bitmapped fonts
GNOME font settings
 * Subpixel smoothing, Full hinting

I think there's been improvement since edgy with newer libfreetype6 and libcairo2.
Font's seem more clear to my eyes and there's less artifacts. Any opinions?

I found to get the best results with the settings you give apart from hinting, which I set to »slight«. I already suggested in that other thread that &#8250;experimental&#8249; is better. I don&#8217;t really think that just moving from Edgy to Feisty changed much, if at all.

---

### Post by mlind on 2007-01-23
> **~LoKe said:**
> What's the url for the key so I can wget it?

Try this
```

gpg --recv-keys 937215FF **--keyserver** subkeys.pgp.net
gpg --export --armor 937215FF | sudo apt-key add -

```

Don't use sudo with gpg commands or you may mess your keyring (~/.gpg directory) privileges

---

### Post by ~LoKe on 2007-01-23
> loke@x04d:~$ gpg --recv-keys 937215FF --keyserver subkeys.pgp.net
gpg: "--keyserver" not a key ID: skipping
gpg: "subkeys.pgp.net" not a key ID: skipping
gpg: no keyserver known (use option --keyserver)
gpg: keyserver receive failed: bad URI
:(

---

### Post by ~LoKe on 2007-01-23
There.  It was backwards.

> gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

---

### Post by mlind on 2007-01-23
> **~LoKe said:**
> There.  It was backwards.

I guess I should add the --keyserver part in the first post, thanks.

---

### Post by mlind on 2007-01-23
> **eremini said:**
> Fonts look good in kde (sans serif), but bad in gnome (got it set to verdana). Which font/size do u recomend using?

I haven't experimented with different font faces at all, but I get weird sized fonts when configuring fontconfig to use Autohinter.
With Native setting, fonts look normal, although I'm using serif family fonts. I bet someone can provide more insightful answer for this.

---

### Post by chrisoverzero on 2007-01-23
> Don't use sudo with gpg commands or you may mess your keyring (~/.gpg directory) privileges

I did not know that...  I retract my previous advice.  *goes off to chown things*

---

### Post by mlind on 2007-01-23
> **chrisoverzero said:**
> I did not know that...  I retract my previous advice.  *goes off to chown things*

I've done it couple of times myself :mrgreen: You can always chown those files back, so it's nothing major though.

---

### Post by andrewski on 2007-01-24
> **mlind said:**
> I'd like to get any feedback about font rendering with freetype2.3[LIST]
[*]After the install, you may want reconfigure font settings. I'm currently using Feisty defaults (Native, Automatic, No bitmapped fonts) myself.[/LIST]OK, I've upgraded, and I definitely see an improvement. So crisp!
I'm using Feisty defaults too, but my GNOME settings went from Slight Hinting, VRGB order to No Hinting, RGB order. (I'm still using Subpixel Smoothing, of course. :)) Just looks better to my eye.

---

### Post by hugmenot on 2007-01-24
Did you rotate your screen when you went from VRGB to RGB? The arrangement of color components on your screen leaves you actually only one sensible option, to use the ordering that your screen has. VRGB on an RGB screen and vice versa leads to a slushy pixel soup.

---

### Post by andrewski on 2007-01-24
> **hugmenot said:**
> Did you rotate your screen when you went from VRGB to RGB? The arrangement of color components on your screen leaves you actually only one sensible option, to use the ordering that your screen has. VRGB on an RGB screen and vice versa leads to a slushy pixel soup.
I just know that before, VRGB with slight hinting looked the best, and now RGB with no hinting looks slightly better. No change in my hardware at all, just the software upgrade here.

I wouldn't mind some other eyes on this; here's a screenshot of the change; the screen on the right is freetype 2.3:
[[IMG]http://img378.imageshack.us/img378/4251/fontdiffs7nf.th.png[/IMG]]("http://img378.imageshack.us/my.php?image=fontdiffs7nf.png")

---

### Post by hugmenot on 2007-01-24
I still don&#8217;t know what alignment you have but RGB is a very save bet since you use a landscape monitor (and not a tablet or something).

I suggest you quickly read up on [a bit of background here]("http://en.wikipedia.org/wiki/Subpixel_rendering") first.

Then, when I clip out some of your screenshot, you&#8217;ll see that earlier VRGB put you in a mode that doesn&#8217;t match with your monitor:

[COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR]
[COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR] [COLOR="Red"]&#9608;[/COLOR][COLOR="Lime"]&#9608;[/COLOR][COLOR="Blue"]&#9608;[/COLOR]

That is your monitor&#8217;s pixel layout, composed of red on the left and blue on the right.

If you now look at your screenshot, you can see that it wants to use a red  &#8531; pixel at the top and the blue subpixel at the bottom. If you turn it 90° ccw it fits.

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=23800&d=1169678296[/IMG]


But honestly without any hinting at all it doesn&#8217;t make a lot of difference after all. The letters just bleed out too much. Think of hinting as some kind of mould in which characters are brought into shape, so that our SR can cleanly shave off a subpixel or two.

---

### Post by andrewski on 2007-01-24
> **hugmenot said:**
> But honestly without any hinting at all it doesn’t make a lot of difference after all. The letters just bleed out too much. Think of hinting as some kind of mould in which characters are brought into shape, so that our SR can cleanly shave off a subpixel or two.
Thanks very much for your reply. I had not read that on Wikipedia before, and I see what you mean about my alignment.

So are you recommending I use some hinting with Linux/Bitstream fonts? My opinion was that they look a bit larger, more "bubbly". But maybe that's what it's supposed to do? Maybe it's a Good Thing(TM)?

---

### Post by hugmenot on 2007-01-24
I can only recommend to play around, also with the font sizes and faces.
Did you check the dpkg-reconfigure screen that mlind mentioned?

---

### Post by andrewski on 2007-01-24
I did but I haven't restarted X since then. I set it to Native and Automatic like mlind did.

---

### Post by eremini on 2007-01-24
[[IMG]http://img242.imageshack.us/img242/8087/snapshot15ui.png[/IMG]](http://imageshack.us)

Mine

---

### Post by hugmenot on 2007-01-24
> Mine
1 0

---

### Post by eremini on 2007-01-24
> **hugmenot said:**
> 1 0

:confused:

---

### Post by mlind on 2007-02-04
upgraded to Freetype 2.3.1.

---

### Post by Footer on 2007-02-07
No packages for amd64:

Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release](http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release)  Unable to find expected entry  experimental/binary-amd64/Packages in Meta-index file (malformed Release file?)

:confused:

---

### Post by mlind on 2007-02-07
> **Footer said:**
> No packages for amd64:

Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release](http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release)  Unable to find expected entry  experimental/binary-amd64/Packages in Meta-index file (malformed Release file?)

:confused:

currently no, sorry. I haven't been able to get cross-build chain to work and no amd64 packages have been sent to me with build logs.

---

### Post by RAOF on 2007-02-07
> **mlind said:**
> currently no, sorry. I haven't been able to get cross-build chain to work and no amd64 packages have been sent to me with build logs.

Just ask me, I'll be willing to build your deb-src for you :).  I'll even host them, if you like.

**EDIT**: Ding!  Now in my repository, under section "experimental".  If you want to mirror them, mlind, they're at [raof.dyndns.org/falcon/pool/feisty/experimental](raof.dyndns.org/falcon/pool/feisty/experimental), and they've got build logs

---

### Post by Footer on 2007-02-08
> **RAOF said:**
> Just ask me, I'll be willing to build your deb-src for you :).  I'll even host them, if you like.

**EDIT**: Ding!  Now in my repository, under section "experimental".  If you want to mirror them, mlind, they're at [raof.dyndns.org/falcon/pool/feisty/experimental](raof.dyndns.org/falcon/pool/feisty/experimental), and they've got build logs

Good news!!!  When will they be available?  These Feisty fonts are hurting my eyes!

:)

---

### Post by mlind on 2007-02-09
> **RAOF said:**
> Just ask me, I'll be willing to build your deb-src for you :).  I'll even host them, if you like.

**EDIT**: Ding!  Now in my repository, under section "experimental".  If you want to mirror them, mlind, they're at [raof.dyndns.org/falcon/pool/feisty/experimental](raof.dyndns.org/falcon/pool/feisty/experimental), and they've got build logs

Excellent, thank you very much! :) I'll update the first post with your amd64 repository if it's okay. I cannot currently automatically mirror the files.

---

### Post by Footer on 2007-02-09
> **mlind said:**
> Excellent, thank you very much! :) I'll update the first post with your amd64 repository if it's okay. I cannot currently automatically mirror the files.

We're getting close ... Now I just need the key:

W: GPG error: [http://raof.dyndns.org](http://raof.dyndns.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651

Thanks!

:)

---

### Post by mlind on 2007-02-09
> **Footer said:**
> We're getting close ... Now I just need the key:

W: GPG error: [http://raof.dyndns.org](http://raof.dyndns.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651

Thanks!

:)

[http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/)
> 
wget [http://raof.dyndns.org/falcon/2F306651.gpg](http://raof.dyndns.org/falcon/2F306651.gpg) -O- | sudo apt-key add -


---

### Post by RAOF on 2007-02-10
> **mlind said:**
> Excellent, thank you very much! :) I'll update the first post with your amd64 repository if it's okay. I cannot currently automatically mirror the files.

That's just fine.  Make sure to emphasise the use of the DE mirror :).

---

### Post by NeoChaosX on 2007-02-10
Just installed Feisty. Since these worked out so great for me in Edgy, these patches were one of the first things I installed. Gorgeous, ClearType-like fonts again. :) 

Now if only it worked on OpenOffice. The program (at least in KDE) still looks like a garbled, blurry mess and renders fonts too small.

---

### Post by hugmenot on 2007-02-14
I found a great tool to test font rendering with. It is "pango-view" from the libpango1.0-dev package.

It can switch between output modules (cairo, xft, gray ft2, and x) hint modes (full, none, auto) and it displays formatted text (pango markup) in a controlled way.

Perhaps we can use this for better objective comparisons?

useful parameters:
--font= (e.g. --font="Trebuchet MS 9")
--dpi
--hinting
--backend
--waterfall
--markup

---

### Post by dentaku65 on 2007-02-14
> **mlind said:**
> 
[*]If you later decide to go back to Ubuntu packages, you must downgrade **all** three installed packages
[*]You'll probably need to restart X-server after installing the packages to see the changes apply


...and how it is possible to go back in the Ubuntu packages? Sorry but I really dislike the fonts that cames out in my terminal....

---

### Post by mlind on 2007-02-14
> **dentaku65 said:**
> ...and how it is possible to go back in the Ubuntu packages? Sorry but I really dislike the fonts that cames out in my terminal....

Use aptitude to remove existing packages, but only accept DOWNGRADE of all three as a solution.
```

sudo aptitude purge libfreetype6 libcairo2 libxft2

```

---

### Post by LadFromWales85 on 2007-02-14
I have to say, followed the steps in the first post to install the experimental packages, and i have to say that I am pleased!

I've tried various other methods of smoothing fonts so that they can look good without glaring obvious sub-pixel hues showing through, including calande's fontconfig XML files which aim to make fonts render like they do in windows, and though his efforts were much better to my eyes than ubuntu edgy/feisty defaults, these packages rock!  Both free linux fonts and windows fonts look very good to my eyes on my LCD now, without the sub-pixels catching my eye when I'm reading.

It's great, thanks, keep it up! :)

---

### Post by eklitzke on 2007-02-19
Apparently poppler is capable of using cairo to do rendering. I really, really want to have evince with subpixel rendering, so I downloaded the poppler source (apt-get source poppler and so forth), changed the rules script to run with --enable-cairo-output (right now it is disabled), and recompiled poppler. But I still get no subpixel rendering in PDF documents. I would sell my soul for this feature -- has anyone gotten it working?

---

### Post by flapane on 2007-02-19
Err [http://raof.dyndns.org](http://raof.dyndns.org) feisty Release.gpg
  Could not connect to raof.dyndns.org:80 (202.63.35.99), connection timed out

---

### Post by mlind on 2007-02-19
> **eklitzke said:**
> Apparently poppler is capable of using cairo to do rendering. I really, really want to have evince with subpixel rendering, so I downloaded the poppler source (apt-get source poppler and so forth), changed the rules script to run with --enable-cairo-output (right now it is disabled), and recompiled poppler. But I still get no subpixel rendering in PDF documents. I would sell my soul for this feature -- has anyone gotten it working?

--enable-cairo-output was excluded for a reason it seems
[http://packages.debian.org/changelogs/pool/main/p/poppler/poppler_0.4.5-5.1/changelog#versionversion0.4.5-3](http://packages.debian.org/changelogs/pool/main/p/poppler/poppler_0.4.5-5.1/changelog#versionversion0.4.5-3)

You probably need to rebuild evince too, against **libpoppler-glib-dev** which you compiled yourself (using --enable-cairo-output). evince looks okay to me, but openoffice is still a mess.

---

### Post by hugmenot on 2007-02-19
[quote=eklitzke]I really, really want to have evince with subpixel rendering...[/quote]

Send your soul to me ASAP.

Based on [this]("http://bugs.freedesktop.org/show_bug.cgi?id=3307") I built the attached packages. They are afflicted with the described clipping problems, but I haven&#8217;t noticed any to be frank.

So, what to do with your soul ...? *ponder, ponder*

[caveats: I disabled KDE stuff for I didn&#8217;t want to clutter my system with dozens of useless libs; If you need the -dev libs shout, the archive got too big with them]

---

### Post by hugmenot on 2007-02-19
> **mlind said:**
> --enable-cairo-output was excluded for a reason it seems
[http://packages.debian.org/changelogs/pool/main/p/poppler/poppler_0.4.5-5.1/changelog#versionversion0.4.5-3](http://packages.debian.org/changelogs/pool/main/p/poppler/poppler_0.4.5-5.1/changelog#versionversion0.4.5-3)


Don&#8217;t see any problems with the bugs cited. Perhaps Cairo was fixed meanwhile?

---

### Post by eklitzke on 2007-02-19
> **hugmenot said:**
> Send your soul to me ASAP.

It's on it's way :-).  Seriously, thanks a lot for pointing me to the patch and building the packages.  I am a math student, and typeset all my work in LaTeX. Math fonts tend to have a lot of serifs and small glyphs (e.g. subscripts and superscripts) that tend to amplify the "bluriness" caused by regular anti-aliasing.  This is a big improvement.

---

### Post by phinn on 2007-02-19
oooh nice, I hope these make it in Feisty final, better fonts wouldn't hurt!

---

### Post by mlind on 2007-02-19
> **hugmenot said:**
> Don’t see any problems with the bugs cited. Perhaps Cairo was fixed meanwhile?

I think this is fixed since poppler 0.5, so using --enable-cairo-output should be safe. It was enabled on 0.5.3-0ubuntu4, but disabled again since 0.5.3-0ubuntu9 with note "the cairo backend is much slower".

Noticed any slowdowns with evince since enabling the feature? If not, I guess you could suggest this enabled as default.

---

### Post by RAOF on 2007-02-19
> **flapane said:**
> Err [http://raof.dyndns.org](http://raof.dyndns.org) feisty Release.gpg
  Could not connect to raof.dyndns.org:80 (202.63.35.99), connection timed out

That's my home box, not guaranteed to be up 24/7.  Use the [ubuntu.moshen.de](ubuntu.moshen.de) mirror instead, that is up 24/7.

---

### Post by hugmenot on 2007-02-19
> **eklitzke said:**
>  Math fonts tend to have a lot of serifs and small glyphs (e.g. subscripts and superscripts) that tend to amplify the "bluriness" caused by regular anti-aliasing.

A piece of advice (pot. sacrilegeous): Dump Computer Modern and use something with less anorectic serifs and &#8220;abgelutschtheit&#8221;. My personal favorite is [MinionPro]("http://developer.berlios.de/projects/minionpro/") currently (comes with acroread 7).
Another hint would be to use pdfLaTeX directly to pdf with Type1 fonts (i.e., \usepackage{lmodern} if you want to stick with the default). DVI and its offspring are always bad on screen.

---

### Post by hugmenot on 2007-02-19
> **mlind said:**
> Noticed any slowdowns with evince since enabling the feature? If not, I guess you could suggest this enabled as default.

Hm, hard to tell. I&#8217;d be cautious with estimations of this kind without controlled benchmarking. Perhaps the Cairo 1.3.1x performance work helped since the deactivation?

---

### Post by flapane on 2007-02-20
> **RAOF said:**
> That's my home box, not guaranteed to be up 24/7.  Use the [ubuntu.moshen.de](ubuntu.moshen.de) mirror instead, that is up 24/7.

thanks
edit: just upgraded, which trick would you suggest to see the differences? I must admit it was quite good, before

---

### Post by mlind on 2007-02-22
> **flapane said:**
> thanks
edit: just upgraded, which trick would you suggest to see the differences? I must admit it was quite good, before

I've been using separate Feisty chroot and opening two instances of same X application, first from normal (chroot) environment, then from current feisty which has patched libraries. 
Easier ways are probably doing screenshots or maybe using method suggested by hugmenot in post [#42]("http://www.ubuntuforums.org/showpost.php?p=2156484&postcount=42"). ftview from freetype2-demos should be useful too.

---

### Post by flapane on 2007-02-23
thanks

---

### Post by flapane on 2007-02-23
it could sound strange, but I feel my eyes very tired using these packages

---

### Post by psyke83 on 2007-02-24
Regarding the terrible fonts in OpenOffice.org, can someone verify if they get these error messages too?

```
conn@inspiron:~$ oowriter
libGL warning: 3D driver claims to not support visual 0x4b

(process:12865): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:12865): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:12865): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:12865): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
conn@inspiron:~$
(process:12865): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:12865): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

I tried downgrading the packages to Feisty's defaults, changing the system font properties back to default, and I can't get the fonts to display any differently (i.e. better).

---

### Post by mlind on 2007-02-25
> **psyke83 said:**
> Regarding the terrible fonts in OpenOffice.org, can someone verify if they get these error messages too?

I tried downgrading the packages to Feisty's defaults, changing the system font properties back to default, and I can't get the fonts to display any differently (i.e. better).

must be caused by something else, I don't get those error messages with or without patched libraries.

---

### Post by hexion on 2007-02-26
Is there any working repository for i386??

The only one that's up is falcon's repo, but it's only for amd64.

Thanks

---

### Post by mlind on 2007-02-26
> **hexion said:**
> Is there any working repository for i386??

The only one that's up is falcon's repo, but it's only for amd64.

Thanks

repositories mentioned on first page work fine for me. what's the problem you're having?

---

### Post by hexion on 2007-02-26
> **mlind said:**
> repositories mentioned on first page work fine for me. what's the problem you're having?

Sorry, it was my fault.. normally before I add a repository to sources.lst, I check the url in firefox.

So I checked [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) and as there's an error message there I supposed the repo was off.

Nevermind, I added that repo and worked well :lolflag:

---

### Post by mlind on 2007-02-26
> **hexion said:**
> Sorry, it was my fault.. normally before I add a repository to sources.lst, I check the url in firefox.

So I checked [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) and as there's an error message there I supposed the repo was off.

Nevermind, I added that repo and worked well :lolflag:

yeah, thanks to my ISP :(

---

### Post by mercurysquad on 2007-03-01
Hey mlind, after the big update from 2 days ago, I now have all the experimental 'turner1e' patches instead of the regular ones .. and I really like the regular ones in the fonts repo, the ones in fonts experimental dont look good to me.

I cheked, and my sources.list still says I am using the fonts repo and not experimental, so any way to get back to the regular patches?

---

### Post by mlind on 2007-03-01
> **mercurysquad said:**
> Hey mlind, after the big update from 2 days ago, I now have all the experimental 'turner1e' patches instead of the regular ones .. and I really like the regular ones in the fonts repo, the ones in fonts experimental dont look good to me.

I cheked, and my sources.list still says I am using the fonts repo and not experimental, so any way to get back to the regular patches?

yeah, I'll put those back again in **legacy** module tomorrow then.

---

### Post by newen on 2007-03-05
Is there any alternative server where I can download the patched packages from?

---

### Post by mlind on 2007-03-05
> **newen said:**
> Is there any alternative server where I can download the patched packages from?

currently no. RAOF hosts amd64 packages though. Are you having problems with the repository?

---

### Post by Slace on 2007-03-05
I can't get the gpg key...

Getting a timeout from the keyserver

---

### Post by sledgehammer89 on 2007-03-12
Try to open on your firewall TCP port 11371

Btw, I get following font error with these patches:
[ATTACH]27247[/ATTACH]

---

### Post by hugmenot on 2007-03-12
That looks really weird. Can you find out which font that is? With vanilla FireFox I don&#8217;t have problems with redhat.com.

---

### Post by sledgehammer89 on 2007-03-12
It's not related to Firefox only. I browsed through my fonts dir and found some other weird fonts.  System: Vanilla Feisty + your repo + MS fonts.
Vanilla Feisty + MS fonts runs well.

I see the same behaviour in Edgy too on only some few webpages, so it doesn't hurt me to much. Now, I'm thinking about what's wrong.
[ATTACH]27259[/ATTACH]

---

### Post by hugmenot on 2007-03-12
If this occurs with fonts from different sources it is likely a bug in Freetype, only that I can&#8217;t reproduce it.

---

### Post by sledgehammer89 on 2007-03-13
Ok, I'll install the "usual" MS fonts only.

I use since years an own "repo" with MS TTF fonts. From time to time, I always replace the newest versions into my font directory. Now, nearly every font is taken from a full installed Vista RC / full installed Office 2k7 RC. So I'm sure I got every font for different tastes.
But as I say, I'll try the usual MS Webfonts today or tomorrow.

---

### Post by andrewski on 2007-03-13
> **mlind said:**
> Are you having problems with the repository?

Yes, for a few days now, your repository hasn't been working. Your ISP did something crazy?

---

### Post by mlind on 2007-03-13
> **andrewski said:**
> Yes, for a few days now, your repository hasn't been working. Your ISP did something crazy?

yeah, sort of. Make sure you're using **fonts** module and remove experimental if you used that previously
```

deb http://www.elisanet.fi/mlind/ubuntu feisty **fonts**

```

@sledgehammer
are you using i386 or amd64 binaries? does that website weirdness happen with epiphany browser too?
(should contain the same rendering engine as firefox)

---

### Post by hugmenot on 2007-03-13
> **sledgehammer89 said:**
> But as I say, I'll try the usual MS Webfonts today or tomorrow.

Yes but your last screenshot shows this corruption also for Luxi Sans, which is clearly not a font from Microsoft. Will it go away if you reverted to the standard libraries?

---

### Post by hugmenot on 2007-03-13
> **mlind said:**
> 
@sledgehammer
are you using i386 or amd64 binaries? does that website weirdness happen with epiphany browser too?
That shouldn&#8217;t make a difference. Moreover, his second screenshot shows the corruption in the Gnome font configuration dialog.

EDIT: Alright, I can confirm for the "Full" setting in the advanced dialog. Must be a bug. It appears in the plain utility ftview as well.

Did this creep in recently?

EDIT2: I went through the list and only see this for the Luxi family, not the MS core fonts and not the ClearType fonts that begin with C.

---

### Post by andrewski on 2007-03-13
> **mlind said:**
> yeah, sort of. Make sure you're using **fonts** module and remove experimental if you used that previously

Yeah, that did the trick. Could you update the first post to remove that? I had checked the repository URL before posting. ;)

---

### Post by hugmenot on 2007-03-13
And it vanishes when I force autohinting in ftview. I&#8217;m gonna report this when I get the time.

---

### Post by sledgehammer89 on 2007-03-14
Ok, the problem goes away when I use MS webfonts only and not my whole private TTF "repository".
About your question: I use i386.

And thank you for debugging (your last posting)!! :)

---

### Post by hugmenot on 2007-03-14
> **sledgehammer89 said:**
> Ok, the problem goes away when I use MS webfonts only and not my whole private TTF "repository".
About your question: I use i386.

And thank you for debugging (your last posting)!! :)

So, which fonts and their version did cause problems? You can read the version in the window that pops up when you double-click a ttf file.
 More info might help to fix this.

---

### Post by bhaagensen on 2007-03-14
mlind, and others who have contributed to the making of these packages. Thanks! It looks great. I've been reluctant to use (more than I already do) third party repos, but as it is now only three packages I thought I'd give it a try. And the result it is really amazing. 

Cheers!

---

### Post by smbm on 2007-03-14
Thanks a lot for this thread. The difference is incredible. What is stopping these improvements being incorporated into Ubuntu?

---

### Post by bhaagensen on 2007-03-14
> **smbm said:**
> Thanks a lot for this thread. The difference is incredible. What is stopping these improvements being incorporated into Ubuntu?

It's an issue with patents. If you're interested try searching on "patent subpixel rendering" in either the forums and google. I think you'll get lots of info.

---

### Post by smbm on 2007-03-15
I'll check it out. Thanks.

---

### Post by hugmenot on 2007-03-15
Here is some info from the horse&#8217;s mouth:
[http://article.gmane.org/gmane.comp.fonts.freetype.user/1912](http://article.gmane.org/gmane.comp.fonts.freetype.user/1912)

---

### Post by hugmenot on 2007-03-18
> **sledgehammer89 said:**
> And thank you for debugging (your last posting)!! :)

I certainly did not 'debug' in the proper sense of that word; I just confirmed; The developers did though and some fixes for TrueType regressions were commited to CVS this weekend. Perhaps those fix your problems. There&#8217;ll be a new release soon.

---

### Post by mlind on 2007-03-20
I think I'm going to compile SVN snapshot once again, there's been few Truetype handling related commits and fix for huge regression in native  bytecode interpreter.

---

### Post by mbelinky on 2007-03-21
Are the repos working? I used the ones on the first page:

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty experimental
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty experimental

and got

Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release](http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release)  Unable to find expected entry  experimental/binary-i386/Packages in Meta-index file (malformed Release file?)

thanks.

---

### Post by Paulus on 2007-03-21
what do you guys think about this?
[http://ubuntuforums.org/showthread.php?t=386661](http://ubuntuforums.org/showthread.php?t=386661)

---

### Post by andrewski on 2007-03-21
> **mbelinky said:**
> Are the repos working? I used the ones on the first page:

deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty experimental
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) feisty experimental

and got

Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release](http://www.elisanet.fi/mlind/ubuntu/dists/feisty/Release)  Unable to find expected entry  experimental/binary-i386/Packages in Meta-index file (malformed Release file?)


Already covered earlier in the thread; the experimental module is no longer available:
> **mlind said:**
> yeah, sort of. Make sure you're using **fonts** module and remove experimental if you used that previously
```

deb http://www.elisanet.fi/mlind/ubuntu feisty **fonts**

```

---

### Post by Joe_Bishop on 2007-03-25
Hi, I have already asked about rendering Cyrillic fonts in Mozilla (gecko?) browsers. You can see difference between Opera and Firefox in one page. Opera rendering is right, because with default font rendering packages this page in Firefox looks similar to Opera. How can I improve this with patched packages?

---

### Post by Pausanias on 2007-03-26
Great work, everybody. Six months ago, using the hand-rolled debs, I found the improvement from the default fonts to be dramatic. But at that time WinXP was still doing a better job.

Now that I've upgraded to feisty, I tried the very latest packages. And my jaw dropped. The improvement on the previous packages is unbelievable. Now I can truly say that we have better font rendering than WinXP (don't know about vista, but I can't imagine that they've fiddled at all with cleartype).

What is the prognosis for challenging the cleartype patent? Alternatively, when will it run out?

---

### Post by mlind on 2007-03-31
Due to ISP change, repository addresses have been changed.
New repositories are
```

deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

```

---

### Post by hugmenot on 2007-04-01
David Turner has posted a preview of his work on improving letter spacing with cached side bearing deltas. It looks very promising but means a new patch fest.
[http://thread.gmane.org/gmane.comp.fonts.freetype.user/2250](http://thread.gmane.org/gmane.comp.fonts.freetype.user/2250)

---

### Post by mlind on 2007-04-01
> **hugmenot said:**
> David Turner has posted a preview of his work on improving letter spacing with cached side bearing deltas. It looks very promising but means a new patch fest.
[http://thread.gmane.org/gmane.comp.fonts.freetype.user/2250](http://thread.gmane.org/gmane.comp.fonts.freetype.user/2250)

yeah, I saw that too. Looks very interesting. This delta stuff doesn't seem to rocket science, so hopefully freetype team will get some help to patch required libraries.

---

### Post by Phantom76 on 2007-04-02
> **mlind said:**
> yeah, I saw that too. Looks very interesting. This delta stuff doesn't seem to rocket science, so hopefully freetype team will get some help to patch required libraries.

mlind, the experimental repository is not working. Can you have a look?

---

### Post by mlind on 2007-04-02
> **Phantom76 said:**
> mlind, the experimental repository is not working. Can you have a look?

yeah, due to recent ISP change new repositories are
```

deb http://www.telemail.fi/mlind/ubuntu feisty **fonts**
deb-src http://www.telemail.fi/mlind/ubuntu feisty **fonts**

```

experimental module is not currently in use. I've updated the fist post to reflect the changes.

---

### Post by RegistrationIsPointless on 2007-04-02
Is anyone maintaining the amd64 versions of this?  The packages in the ubuntu.moshen.de repository are too ancient to use with the Feisty beta, and the RAOF repository recommended in the first post is simply inaccessible (looks like it's a home PC, so I guess it must be turned off whenever I'm online.)

Would really appreciate it if someone could put up-to-date amd64 packages on a reliable server... being forced to choose between blurriness or rainbow-colored fringes is beginning to get me down.  :(

---

### Post by gbesso on 2007-04-03
My server is currently being moved, I will put one up once it's up, it should be a few days.

---

### Post by RAOF on 2007-04-04
> **RegistrationIsPointless said:**
> Is anyone maintaining the amd64 versions of this?  The packages in the ubuntu.moshen.de repository are too ancient to use with the Feisty beta, and the RAOF repository recommended in the first post is simply inaccessible (looks like it's a home PC, so I guess it must be turned off whenever I'm online.)
...

There'll be a sync from raof.dyndns.org to moshen.de, just as soon as I strip all the **really** experimental stuff from there :).

---

### Post by Joe_Bishop on 2007-04-04
So, I have told about enormously large fonts with patched libxft in Gecko browsers already.  I notice, if unmark checkbox "Allow pages to choose their own fonts...", the fonts size becames normal, but it is the sort of hack, and does not satisfy me completely, because pages look different as they should be (another fonts).

---

### Post by hardhu on 2007-04-05
Hello everybody,
I am a kubuntu feisty amd64 user. I have followed the steps suggested in the first post (with the only difference of using deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental repository, since the amd64 suggested one seems not up at present time), but I see no difference in font rendering in my kde applications, while I can see it in Firefox that I have installed in a feisty 32bit chroot where I followed the same procedure. Is it because of the packages for amd64 in the repository are older than official feisty ones (except for libfreetype6) or am I missing something else?

---

### Post by mlind on 2007-04-05
> **hardhu said:**
> Hello everybody,
I am a kubuntu feisty amd64 user. I have followed the steps suggested in the first post (with the only difference of using deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental repository, since the amd64 suggested one seems not up at present time), but I see no difference in font rendering in my kde applications, while I can see it in Firefox that I have installed in a feisty 32bit chroot where I followed the same procedure. Is it because of the packages for amd64 in the repository are older than official feisty ones (except for libfreetype6) or am I missing something else?

I guess the amd64 packages aren't sync with i386 packages repository. If Ubuntu releases an update for libcairo or xft, those packages are considered newer and will get installed. You can either rebuild amd64 versions from the source packages in my repository or use apt pinning for current patched amd64 packages.

You probably have Ubuntu provided libcairo2 installed since the package was updated recently and that's why you don't see any improvements. You can check this out using numerous ways, using apt-cache for example
```

apt-cache policy libcairo2
apt-cache madison libcairo2

```

if you want to rebuild the packages, easiest way is to probably use autobuilder like pbuilder or sbuild.

---

### Post by RAOF on 2007-04-07
Yeah, sorry.  I just noticed that libcairo2 FTBFS for me (and there's a new version, too).  New packages should be built soon.

---

### Post by mlind on 2007-04-07
> **RAOF said:**
> Yeah, sorry.  I just noticed that libcairo2 FTBFS for me (and there's a new version, too).  New packages should be built soon.

thanks for your efforts on this.
I changed to am64 repository link to point the [http://ubuntu.moshen.de](http://ubuntu.moshen.de) instead.

---

### Post by mech7 on 2007-04-09
Does this really work? are there any screens as i now just put it to monoschrome as otherwise it looks sorta crap 0_o

---

### Post by mlind on 2007-04-09
> **mech7 said:**
> Does this really work? are there any screens as i now just put it to monoschrome as otherwise it looks sorta crap 0_o

for me at least, the difference is very much noticeable. Dunno how you've configured your font settings, but I'd suggest to browse earlier post and hugmenot's Edgy thread too for reference.

---

### Post by psyke83 on 2007-04-09
Hi,

Take a look at the following screenshots:

Greyscale rendering, medium hinting:
[IMG]http://connogriofa.googlepages.com/Greyscale-Medium.png[/IMG]

Subpixel rendering, slight hinting: [IMG]http://connogriofa.googlepages.com/Subpixel-Slight.png[/IMG]

As you can see, OpenOffice.org renders fonts differently than the rest of the system. In the first screenshot, OpenOffice's fonts look good, but the rest of the system's font's don't, and with the second picture, the latter is true.

Is there a way to make OpenOffice use a different .fonts.conf file than the rest of the system? I was thinking of writing a script that copies a .fonts.conf file that uses greyscale/medium hinting, launches oowriter and then deletes the file again (to prevent other apps from rendering with those settings). Is there a better way, perhaps an environment variable to specify a custom .fonts.conf?

---

### Post by mlind on 2007-04-09
@ psyke83
Yes, this is known issue and would probably require patching and rebuilding of openoffice which is not a fun thing to do.
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html)
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html)
[http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html](http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html)

There's a patch for older openoffice @ [http://freetype.org/freetype2/patches/rogue-patches.html](http://freetype.org/freetype2/patches/rogue-patches.html), but I don't think it will apply for OO 2.2.
[http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html](http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html)

Try to recompile freetype source package and disable the bytecode interpreter
(by commenting *freetype-bytecode-interpreter.patch* from **debian/patches-freetype/series** file)
[http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html](http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html)

---

### Post by dcherryholmes on 2007-04-12
Could anyone give me a hand in undoing this?  I tried commenting out the debs from /apt/sources.list and updating/upgrading, but it didn't revert.  I tried apt-get --reinstall and got this:

root@valar:~# apt-get install --reinstall libfreetype6
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reinstallation of libfreetype6 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I had planned to go through all three packages that were upgraded after the sources.list change, expecting them to be forced back to their original versions.  I also thought maybe I could just dpkg -i the old packages out of /var/cache/apt/archives, but there actually wasn't an older version of libxft2.

Any suggestions?

---

### Post by mlind on 2007-04-12
> **dcherryholmes said:**
> Could anyone give me a hand in undoing this?  I tried commenting out the debs from /apt/sources.list and updating/upgrading, but it didn't revert.  I tried apt-get --reinstall and got this:

root@valar:~# apt-get install --reinstall libfreetype6
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Reinstallation of libfreetype6 is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I had planned to go through all three packages that were upgraded after the sources.list change, expecting them to be forced back to their original versions.  I also thought maybe I could just dpkg -i the old packages out of /var/cache/apt/archives, but there actually wasn't an older version of libxft2.

Any suggestions?

You can install other version from a repository if you explicitly define the version.
To install Ubuntu's (current) packages
```

sudo aptitude install libfreetype6=2.2.1-5ubuntu1 libcairo2=1.4.2-0ubuntu1 libxft2=2.1.12-1

```

For instance, you can use *apt-cache madison libfreetype6* (and *apt-cache policy libfreetype6*) to find out what versions of libfreetype6 are available in the repositories you've defined in your sources.list.

---

### Post by hugmenot on 2007-04-12
Or, if you&#8217;re a GUI type use Synaptic. Go to the "Sources" section and locate telemail.fi or elisanet.fi. There, just walk through the packages and force the official Ubuntu package in the Versions tab.

---

### Post by mlind on 2007-04-12
> **hugmenot said:**
> Or, if you&#8217;re a GUI type use Synaptic. Go to the "Sources" section and locate telemail.fi or elisanet.fi. There, just walk through the packages and force the official Ubuntu package in the Versions tab.

hum.. I guess I should learn to use Synaptic someday :mrgreen:
It seems to have gained some of the super-cow powers since I last time gave it a spin.

---

### Post by hugmenot on 2007-04-12
I figured that out when the question arose in that other thread.
Myself, I favor aptitude xxx.

---

### Post by njee on 2007-04-19
I fiddled around with the settings and was able to reach a compromise I think.

New free type packages applied, 

fontconfig was autohinter, always, no

font settings were simply set to best shapes.


This was it seems both the desktop and openoffice get antialiased. The fonts don't look exactly the same, but I'm happy with the outcome.

---

### Post by buttons on 2007-04-20
I just did a dist upgrade from edgy to feisty, and I can say it DOES actually look like there are fewer colour artifacts, and it's quite pleasant to look at.

Except, I sometimes have a problem where letters near the 'f' character kinda merges with a surrounding character...difficult to describe.

See attached image for the words "official" and "figurative."

I have observed it on other sites as well.

---

### Post by buttons on 2007-04-20
Update: FIXED.  Disabling pango makes the letters space more evenly now.  Interesting.

---

### Post by hmsf on 2007-04-21
Worked very well for me!! :) 

Just OpenOffice that still is a little weird.. the menus are fine, but the text area still shows very bad fonts.. I'm subscribing this thread, maybe someone will find a solution...

---

### Post by gnomeuser on 2007-04-21
I think we can put this in universe and offer it side-by-side the official Freetype as an add-on. The following Fedora package (via livna.org) implements this concept:

[https://bugzilla.livna.org/show_bug.cgi?id=1473](https://bugzilla.livna.org/show_bug.cgi?id=1473)

Should be easy to adapt.

---

### Post by Paool on 2007-04-21
(edited, pls remove this post)

---

### Post by mo0nl0rd on 2007-04-22
i keep getting this on bash

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg: requesting key 937215FF from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect: eof
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any way so that i can wget it instead?

---

### Post by mlind on 2007-04-22
> **mo0nl0rd said:**
> i keep getting this on bash

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg: requesting key 937215FF from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 7: couldn't connect: eof
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any way so that i can wget it instead?

Did you try another keyserver ?
```

--keyserver keyserver.ubuntu.com

```
([or get it using browser]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xD0AFFF5E937215FF"))

---

### Post by c4mden on 2007-04-22
> **mlind said:**
> Did you try another keyserver ?
```

--keyserver keyserver.ubuntu.com

```
([or get it using browser]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xD0AFFF5E937215FF"))

didn't work for me either, but 
```

gpg --keyserver keyserver.veridis.com --recv-keys 937215FF

```
worked juse fine

---

### Post by sinistertim101 on 2007-04-23
I did all these things with edgy with wonderful results for my laptop.

WIth Fiesty its not the same and the fonts look very thin even with the same mscore font and davids freetype patches.

---

### Post by tist on 2007-04-23
Is there any chance of powerpc packages coming out?

That would be extremely nice for an ageing powerbook G3 that's been given a life extension with xubuntu.

---

### Post by mlind on 2007-04-23
> **tist said:**
> Is there any chance of powerpc packages coming out?

That would be extremely nice for an ageing powerbook G3 that's been given a life extension with xubuntu.

If I only had access to powerpc machine, but unfortunately I don't :(
You can rebuild the packages from source yourself though. I can walk you though the process if you're interested.

---

### Post by uterrorista on 2007-04-24
**can someone post a [COLOR="Red"]printscreen[/COLOR] of the final result please...**?!
Thanks

---

### Post by Mlehliw on 2007-04-24
Here are my before and after pics, I used Native, Automatic, No bitmapped fonts, like the OP. Maybe I did something wrong but I like the original fonts better, the new ones are too "fuzzy" for me.

The left picture is the before picture, and on the right is the after picture by the way.

---

### Post by xopher on 2007-04-25
> **Mlehliw said:**
> Here are my before and after pics, I used Native, Automatic, No bitmapped fonts, like the OP. Maybe I did something wrong but I like the original fonts better, the new ones are too "fuzzy" for me.

The left picture is the before picture, and on the right is the after picture by the way.

This is the case for me too I guess - my fonts became fuzzier after I installed the updates.

To revert - I just downgrade the packages and reconfigure fontconfig again? Or do I need to do something else?

Edit: Worked fine to downgrade; restart X..

---

### Post by Joe_Bishop on 2007-04-25
Does anyone know what I should do? You can see 2 shots, one with slight hinting, and another one with no hinting. With slight hinting letter are little greater than they should be, while with no hinting they has right sizes. But with no hinting letter are too blurry. It happens with both Cyrillic and Latin letters.

---

### Post by FrancoNero on 2007-04-26
ok I am slightly confused about this thread. if i enable lcd fonts in feisty, it doesn't work and that's why this thread exists? in those two screenshots above i dont really see any differences.

---

### Post by andrewski on 2007-04-26
> **Joe_Bishop said:**
> Does anyone know what I should do? You can see 2 shots, one with slight hinting, and another one with no hinting. With slight hinting letter are little greater than they should be, while with no hinting they has right sizes. But with no hinting letter are too blurry. It happens with both Cyrillic and Latin letters.
I know what you mean; the letters do look a bit bigger but have better shapes and edges. Ultimately, I got used to it. The letters, IMO, look rather uniform and nice. I have a hard time using fonts on Windows now; they look so clunky.

---

### Post by hugmenot on 2007-04-26
> **FrancoNero said:**
> ok I am slightly confused about this thread. if i enable lcd fonts in feisty, it doesn't work and that's why this thread exists?
   This thread existed originally because patches appeared that improved fonts beyond the old and default LCD stuff. Meanwhile those improvements were integrated into the library, but they are disabled because it  became clear that  it makes distros vulnerable to patent claims if enabled by default. The technology used before was affected just the same, that&#8217;s why any kind of subpixel filtering is disabled now.   
 
   > in those two screenshots above i dont really see any differences.The difference lies in the hinting. On the left you see more sharp letters, while on the right hand side you have more curves and shape preserved at the expense of contrast/sharpness.

---

### Post by QCompson on 2007-04-30
In my opinion, this has improved the quality of my fonts tremendously in Feisty.  I have a LCD screen, and prior to taking these steps I found Ubuntu's fonts to be woefully inferior to the font appearance in windows.  Now Ubuntu's fonts are nearly as good.  Thanks OP!

ps - Open Office fonts still look like crap

---

### Post by mr_firefox on 2007-05-01
AbiWord fonts look great - so as a result I have ditched oowriter for now!

---

### Post by mlind on 2007-05-02
Yeah, that ooffice issue is a shame. There's a bugreport on [DBTS]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=385798") which is closed as 'fixed', but it seems the issue is present in Etch too.

Have you tried using LD_PRELOAD with Ubuntu's libfreetype.so.6?
Here's a quick howto for testing
```

mkdir /tmp/libfreetype6
cd /tmp/libfreetype6
aptitude download libfreetype6=2.2.1-5ubuntu1
dpkg -x *.deb .
cp -a $(find . -name '*.6*') .
**LD_PRELOAD=/tmp/libfreetype6/libfreetype.so.6** oowriter

```
if this makes any difference, place the .sonames in safe place and use LD_PRELOAD to launch ooffice from now on.
(You probably don't need the symlink file).

---

### Post by Randall311 on 2007-05-02
Hi mlind. Thanks for this great thread! I was able to get the patches working perfectly in ubuntu (gnome) then I decided to try the lightweight desktop xfce. I installed xubuntu on top of my working ubuntu config using ```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` and now my font rendering has reverted to the out of the box default somehow. I'd assume that these patches should work for any gtk-2 app using cairo and freetype etc, but either that's not the case, or the patches got overwritten somehow. Do you have any suggestions? Should I repeat the entire process after I install xfce, or is there a simple fix?  I tried apt-get update in hopes that I would pick up the patches again, but no luck. Any advice is appreciated.

 Thanks,
Justin

---

### Post by hugmenot on 2007-05-02
Could it be that Xfce just switched your font display back to grayscale antialias?
Did you check their version of the font preferences?
Otherwise just type "apt-cache policy libfreetype6" into a terminal and check the installed version.

---

### Post by LuisGMarine on 2007-05-02
Hello,

Just another user dropping by and thanking the community, and the author for these great posts.  For me personally I was starting to freak out at how the text was being rendered so badly.  Nice to see the fonts so close, excuse me I should correct myself, SO MUCH BETTER than the fonts in windows.  

Anyhow thanks a lot to all of you out there that made this happen.  

By the way, there are people out there, including myself , who are having issues with fonts not being rendered properly in Firefox, you think this can fix it?  For me it did slightly, but it could be just a figment of my imagination, I didn't really have any hardcore evidence to prove that it actually did improve anything.  Let me know if you guys know what is up, seems like a lot of peoples Firefox is breaking down as far as the text goes ....

Good Luck

-LuisGMarine :guitar:

---

### Post by Randall311 on 2007-05-03
> **hugmenot said:**
> Could it be that Xfce just switched your font display back to grayscale antialias?
Did you check their version of the font preferences?
Otherwise just type "apt-cache policy libfreetype6" into a terminal and check the installed version.

Hmm that is a possibility. When I get home I will check and post back. Thanks for taking the time to help me.


Yes that was it. Thanks for your help!

---

### Post by mlind on 2007-05-04
> **LuisGMarine said:**
> 
By the way, there are people out there, including myself , who are having issues with fonts not being rendered properly in Firefox, you think this can fix it?  For me it did slightly, but it could be just a figment of my imagination, I didn't really have any hardcore evidence to prove that it actually did improve anything.  Let me know if you guys know what is up, seems like a lot of peoples Firefox is breaking down as far as the text goes ....


Hiya,
what do you exactly mean fonts aren't rendering properly with firefox? Does this happen only with patched libraries? What fonts have you configured for firefox? Does this happen with certain fonts only? What system-wide locale are you using? 

Does disabling pango for firefox have any effect (it's probably already disabled) ?
```

MOZ_DISABLE_PANGO=1 firefox

```

---

### Post by SigmundFreud on 2007-05-04
These patches improved the fonts on my Kubuntu installation a lot. Since I don't use Bitstream Vera that much, I made a few different choices than you suggest. Also, a reboot/X restart doesn't seem to be necessary. Thank you.

---

### Post by LuisGMarine on 2007-05-04
> **mlind said:**
> Hiya,
what do you exactly mean fonts aren't rendering properly with firefox? Does this happen only with patched libraries? What fonts have you configured for firefox? Does this happen with certain fonts only? What system-wide locale are you using? 

Does disabling pango for firefox have any effect (it's probably already disabled) ?
```

MOZ_DISABLE_PANGO=1 firefox

```

All good now, for some reason the fonts seemed to either get fixed by your guide here, or they did it on their own.  All is back to well now, thanks a lot for this great tutorial and I hope to hear more fixes from you :)  This is deff going into my record book!

Thanks! :guitar:

---

### Post by benjaminzsj on 2007-05-06
Hi, firstly thanks for the work.
I follow the instructions Native Always No, but still got the effect like in [this post]("http://ubuntuforums.org/showpost.php?p=2059503&postcount=29"), what have I done wrong? I'm using san serif font.

---

### Post by stivani on 2007-05-06
> **benjaminzsj said:**
> Hi, firstly thanks for the work.
I follow the instructions Native Always No, but still got the effect like in [this post]("http://ubuntuforums.org/showpost.php?p=2059503&postcount=29"), what have I done wrong? I'm using san serif font.
You have to enable anti-aliasing. Go to systemsettings > appearance > fonts and enable the option "use anti-aliasing for fonts and probably also sub-pixel hinting under configure.

---

### Post by benjaminzsj on 2007-05-06
> **stivani said:**
> You have to enable anti-aliasing. Go to systemsettings > appearance > fonts and enable the option "use anti-aliasing for fonts and probably also sub-pixel hinting under configure.

Yeah, I have already enabled them, and weird thing is that many other fonts look great, e.g. bitstream sans, but no luck with sans serif.:confused:

---

### Post by mlind on 2007-05-06
> **benjaminzsj said:**
> Yeah, I have already enabled them, and weird thing is that many other fonts look great, e.g. bitstream sans, but no luck with sans serif.:confused:

is this only with firefox (and other mozilla applications) ?

what's the output of
```

apt-cache policy libxft2 libcairo2 libfreetype6 | grep -i installed

```

---

### Post by benjaminzsj on 2007-05-06
> **mlind said:**
> is this only with firefox (and other mozilla applications) ?

what's the output of
```

apt-cache policy libxft2 libcairo2 libfreetype6 | grep -i installed

```
```
Installed: 2.1.12-2~turner1
  Installed: 1.4.6-1~turner1
  Installed: 2.3.4-0mlind1

```
No, it's with all the KDE programs as well as firefox. And bold fonts in firefox seem antialiased.

---

### Post by digital_k on 2007-05-07
Thank you very much for this how-to. It could not get any easier! :KS

---

### Post by schlifers on 2007-05-07
Hi,
 I kinda got these to work with debian sid, is there anyway you could repackage and host a repo for debian users? :D btw libxft2 has been upgraded in fiesty and in sid so an update would be appreciated.
Thanks

---

### Post by nohairleft on 2007-05-08
Now there is bling, and there is BLING! this little how to guide would have to be one of the best threads around for eye candy...

Awesome guys and gals, I have been tearing my hair out over the messy fonts on my TFT, was ready just to sit back and accept it. NOT now  :KS :KS :KS :KS :KS :KS :KS

Cheers :)

---

### Post by mlind on 2007-05-08
> **benjaminzsj said:**
> ```
Installed: 2.1.12-2~turner1
  Installed: 1.4.6-1~turner1
  Installed: 2.3.4-0mlind1

```
No, it's with all the KDE programs as well as firefox. And bold fonts in firefox seem antialiased.

Sorry I can't help you with KDE specific stuff. Maybe someone else knows better.
Packages look okay.

---

### Post by mlind on 2007-05-08
> **schlifers said:**
> Hi,
 I kinda got these to work with debian sid, is there anyway you could repackage and host a repo for debian users? :D btw libxft2 has been upgraded in fiesty and in sid so an update would be appreciated.
Thanks

I'll see what I can do.

The libxft2 was upgraded a while ago, so we're in sync with sid's and gutsys's libxft2.

---

### Post by benjaminzsj on 2007-05-08
> **mlind said:**
> Sorry I can't help you with KDE specific stuff. Maybe someone else knows better.
Packages look okay.
I see. Can you please post your .fonts.conf? Thanks.

---

### Post by mlind on 2007-05-09
> **benjaminzsj said:**
> I see. Can you please post your .fonts.conf? Thanks.

I don't override the defaults, so I don't have one.

---

### Post by nosebleed on 2007-05-09
> **mlind said:**
> I'll see what I can do.

The libxft2 was upgraded a while ago, so we're in sync with sid's and gutsys's libxft2.

Hey man, I'm trying out gutsy and it's preferring the official (unpatched) versions over yours and when I try to force versions, it wants to uninstall some packages I depend on. Any ideas on how to get your version to the front of the line, so to speak?

---

### Post by RAOF on 2007-05-10
You'd want to extract the patches from the patched version, and rebuild Gutsy's source packages with those patches added.  It'd probably be pretty simple, and if you're running Gutsy at this point, you should be able to do it :P

---

### Post by Lucifiel on 2007-05-10
> **mlind said:**
> @ psyke83
Yes, this is known issue and would probably require patching and rebuilding of openoffice which is not a fun thing to do.
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html)
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html)
[http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html](http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html)

There's a patch for older openoffice @ [http://freetype.org/freetype2/patches/rogue-patches.html](http://freetype.org/freetype2/patches/rogue-patches.html), but I don't think it will apply for OO 2.2.
[http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html](http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html)

Try to recompile freetype source package and disable the bytecode interpreter
(by commenting *freetype-bytecode-interpreter.patch* from **debian/patches-freetype/series** file)
[http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html](http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html)
Omg, being someone who had this issue too(like Psyke83)... nooo I have to recompile Open office?! That's just terrible. Actually, my problem is that after my user profiles became corrupted, all my fonts looked corrupted in Firefox and various programs, etc.  I'd to add in the following text into my fonts.conf to solve the corrupted fonts issue.
"<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>"

The issue was then solved but then a few days later, Open Office started to have a corrupted font display too. Uninstalling the font packages mentioned in this guide didn't exactly work nor did reinstalling Ooffice. 

Ah well, I guess I'll just stick to my workaround which sets the Zoom view at a value (110% and above) which isn't the best option, though. :( But still, the text is at least less painful on my eyes.

---

### Post by mlind on 2007-05-10
@ Lucifiel
For openoffice, did you try Using Ubuntu's libfreetype6.so as described in post [#140]("http://ubuntuforums.org/showpost.php?p=2578642&postcount=140") ?

For some reason, my openoffice fonts look "okay" and I'm not using any customized stuff (except the patched libs).

---

### Post by Mitlik on 2007-05-10
My open office still looks the same, though I must say the rest of Kubuntu is looking pretty dang sweet. So I tried the sugguestion by mlind in [#140]("http://ubuntuforums.org/showpost.php?p=2578642&postcount=140") and I get this error:
```
/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/libXft.so.2:
   undefined symbol: FT_Library_SetLcdFilter

** (process:10984): WARNING **: Unknown error forking main binary / abnormal early exit ...
```
Is there another way around it?

---

### Post by Lucifiel on 2007-05-10
> **mlind said:**
> @ Lucifiel
For openoffice, did you try Using Ubuntu's libfreetype6.so as described in post [#140]("http://ubuntuforums.org/showpost.php?p=2578642&postcount=140") ?

For some reason, my openoffice fonts look "okay" and I'm not using any customized stuff (except the patched libs).

Ehhh... well kinda missed that post! 

Hmmm... *goes to try the steps listed*

Ah, it still looks the same. *sighs* 

At this rate, I'll have to give KOffice a shot. I just don't have the time to keep tinkering around with Ooffice anymore.  

What a shame, though 'cos Ooffice just is better KWriter at this point.

---

### Post by Lucifiel on 2007-05-11
Hmmm just reinstalled Open office. Hmmm... the problem is still there, though.

---

### Post by mlind on 2007-05-11
> **Lucifiel said:**
> Hmmm just reinstalled Open office. Hmmm... the problem is still there, though.

@ Mitlik
I'm not sure why KDE is complaining about missing FT_Library_SetLcdFilter. Are you sure you've got patched libxft2 installed too ?

@ Lucifiel
I guess the only way you can fix oo to respect freetype internals is to apply patch from related openoffice upstream bugreport, that's pending merge to main trunk (and rebuild :() or try using LD_PRELOAD with libfreetype.so.6 version that works. Other than that, I dunno.

---

### Post by Lucifiel on 2007-05-12
> **mlind said:**
> @ Mitlik
I'm not sure why KDE is complaining about missing FT_Library_SetLcdFilter. Are you sure you've got patched libxft2 installed too ?

@ Lucifiel
I guess the only way you can fix oo to respect freetype internals is to apply patch from related openoffice upstream bugreport, that's pending merge to main trunk (and rebuild :() or try using LD_PRELOAD with libfreetype.so.6 version that works. Other than that, I dunno.

Oh my goodness... lol.

Being a newbie, I'd have to say that doesn't make any sense to me.  What trunk? What internals? 

Sorry. :p

Thank you for your help so far. :) I'll keep looking around. :)

---

### Post by hnfmr on 2007-05-16
Please please....provide a way for me to get back to my original Ubuntu (Feisty) settings

My fonts look much more uglier after applying your techniques @_@ (Especially inFireFox)

please help...

---

### Post by mlind on 2007-05-17
> **hnfmr said:**
> Please please....provide a way for me to get back to my original Ubuntu (Feisty) settings

My fonts look much more uglier after applying your techniques @_@ (Especially inFireFox)

please help...

```

sudo aptitude install libfreetype6=2.2.1-5ubuntu1 libcairo2=1.4.2-0ubuntu1 libxft2=2.1.12-1

```

btw. Did you enable subpixel smoothing from your font settings?

---

### Post by t_anjan on 2007-05-18
I wonder why this hasn't been mentioned before.

Has anyone else noticed that on Feisty64, installing these patched subpixel rendering packages (the 64b versions), improves the font rendering on the 64b applications ONLY. For example, Opera looks horrible.

A workaround for this is to download the 32b debs and manually extract the data.tar.gz inside the debs into **/usr/lib32** . This patches even the 32b versions of libcairo, libfreetype and libxft. Only after doing this did my 32b apps (on Feisty64) look good, like the rest of Ubuntu.

Shouldn't this be an automated process when installing the 64 bit packages?

---

### Post by screaminj3sus on 2007-05-18
Wow thank you very much for this guide makes ubuntu much more enjoyable to use on my LCD, one of the most annoying things about linux for me was always the fonts.

---

### Post by zerwas on 2007-05-20
Will these patches get default in Gutsy Gibbon?

---

### Post by RAOF on 2007-05-22
> **t_anjan said:**
> ...
A workaround for this is to download the 32b debs and manually extract the data.tar.gz inside the debs into **/usr/lib32** . This patches even the 32b versions of libcairo, libfreetype and libxft. Only after doing this did my 32b apps (on Feisty64) look good, like the rest of Ubuntu.

Shouldn't this be an automated process when installing the 64 bit packages?

Only if I made the packages build those 32bit libs, and replace the files from ia32-libs-gtk (or wherever they come from).  I use so few 32bit programs (and the ones that I **do** use are run in wine) that it's not something I'm particularly interested in.  Debdiffs welcome! :)

[quote=zerwas]Will these patches get default in Gutsy Gibbon?[/quote]

They **still** almost certainly infringe some Microsoft cleartype patents.  As such, the overwhelmingly likely answer is "no".

---

### Post by isenalim on 2007-05-22
Hi,
these fonts are really beautiful! 
They only have one major problem: pdf files look horrible! I have tried evince, xpdf, kdfp and adobe reader and they all look very very ugly and hardly readable! I read many pdfs at work and I am afraid I will have to switch back to the original fonts if there isn't any fix...
Do you have any hint?
Thanks a lot!
I

---

### Post by hmsf on 2007-05-22
This was added today in [Mark Shuttleworth's blog]("http://www.markshuttleworth.com/archives/119"):

> Anybody else frustrated with the state of fonts in Linux today?

It seems there are two distinct issues: the availability of high quality fonts under Free licenses, and the infrastructure for installing, managing and accessing those fonts.

There has been some progress on both fronts. Bitstream’s Vera, and the new [Liberation font]("http://www.press.redhat.com/2007/05/09/liberation-fonts/") work (kudos to Red Hat for driving that effort) are steps to provide us with a clean, crisp set of high quality fonts with good hinting that can be installed by default. There is also good work being done by, amongst others, [SIL International]("http://www.sil.org/") on a [free font license]("http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=OFL_web") framework, and fonts to go with it. I hope the community can build on these efforts to expand the font coverage to the full Unicode glyphset, preserving their essential character and metrics.

The second problem, the infrastructure and API’s to manage fonts on Linux systems, is more complicated. Here’s a [mail to the ubuntu-devel list]("https://lists.ubuntu.com/archives/ubuntu-devel/2007-May/023623.html") describing the situation and calling for leadership from the community in helping to address it.

We need a clean, clear way of:

   1. Packaging fonts, and knowing which packages to install to get which fonts.
   2. Cataloguing fonts, and allowing people to manage the fonts that are immediately accessible to them or loaded by default, everywhere.
   3. Making all of this sane in a world where you MIGHT want to read a document in Korean using a French desktop. In other words, where there need to be a lot of fonts available, even if most of those fonts are not used all the time.

Most of the long list of fonts I see in OpenOffice are lost on me, I don’t know when I would choose any of them.

Sounds like a mess, but then again it also sounds like the sort of Gordian knot that the flaming sword of free software leadership can slice straight through, given strong leadership and a forum for the work. Who will step up?

Thought it might interest some of you...

---

### Post by Lieter on 2007-05-22
hi, ive installed this but it doesnt work, in preferences->fonts ive selected sub-pixel smoothing and full. but my FF and titlebars in beryl(i use heavy AA'd lucida mac on metacity). On my laptop i havnt installed these fonts in this thread and the same beryl bar looks fine. whats up with that

here are 2 pictures showing it:
[img]http://lieter.isdeshit.nl/img/ubuntu/desktop.png[/img]
(desktop)

[img]http://lieter.isdeshit.nl/img/ubuntu/laptop.png[/img]
(laptop)

the same font ugliness is true for FF, works on lappy, not on desktop

---

### Post by hugmenot on 2007-05-22
Time for a security patch upload?
[http://www.heise-security.co.uk/news/90040](http://www.heise-security.co.uk/news/90040)

---

### Post by mlind on 2007-05-22
> **hugmenot said:**
> Time for a security patch upload?
[http://www.heise-security.co.uk/news/90040](http://www.heise-security.co.uk/news/90040)

yup. thanks for the heads up.

---

### Post by skip27 on 2007-05-28
> **mlind said:**
> @ psyke83
Yes, this is known issue and would probably require patching and rebuilding of openoffice which is not a fun thing to do.
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00050.html)
[http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html](http://lists.gnu.org/archive/html/freetype/2006-09/msg00083.html)
[http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html](http://lists.gnu.org/archive/html/freetype-devel/2006-11/msg00013.html)

There's a patch for older openoffice @ [http://freetype.org/freetype2/patches/rogue-patches.html](http://freetype.org/freetype2/patches/rogue-patches.html), but I don't think it will apply for OO 2.2.
[http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html](http://lists.gnu.org/archive/html/freetype-devel/2006-05/msg00064.html)

Try to recompile freetype source package and disable the bytecode interpreter
(by commenting *freetype-bytecode-interpreter.patch* from **debian/patches-freetype/series** file)
[http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html](http://lists.gnu.org/archive/html/freetype-devel/2003-04/msg00031.html)

I actually have some insights into this and have the solution. Well... I don't actually solve the problem per-se, but I explain exactly why it can't be solved.

[http://ubuntuforums.org/showpost.php?p=2711061&postcount=19](http://ubuntuforums.org/showpost.php?p=2711061&postcount=19)

The short version: oo.org, presently, is not fully compatible with Freetype versions later than 2.1.10 (libfreetype.so.6.3.8 ). If you attempt to compile oo.org against the Turner Freetype libraries, which is what I did, ooo simply defaults to LCD subpixel rendering while completely DISABLING hinting. Unless David Turner is willing to apply his magic to the Freetype 2.1.10 libraries, we'll be stuck until the oo.org team revises the code to make it recognize the changes in the later Freetype releases.

---

### Post by mlind on 2007-05-28
> **skip27 said:**
> I actually have some insights into this and have the solution. Well... I don't actually solve the problem per-se, but I explain exactly why it can't be solved.

[http://ubuntuforums.org/showpost.php?p=2711061&postcount=19](http://ubuntuforums.org/showpost.php?p=2711061&postcount=19)

The short version: oo.org, presently, is not fully compatible with Freetype versions later than 2.1.10 (libfreetype.so.6.3.8 ). If you attempt to compile oo.org against the Turner Freetype libraries, which is what I did, ooo simply defaults to LCD subpixel rendering while completely DISABLING hinting. Unless David Turner is willing to apply his magic to the Freetype 2.1.10 libraries, we'll be stuck until the oo.org team revises the code to make it recognize the changes in the later Freetype releases.

Yeah, there's a bug in oo upstream about this and I reckon there's not much to be done until the bug is sorted out. Have you tried LD_PRELOADing older libfreetype6 library when launching ooffice btw? There's a bug In DBTS in which few people confirm that this workaround actually works.

Thanks for your insightful post on the other thread btw.

---

### Post by skip27 on 2007-05-29
> **mlind said:**
> Yeah, there's a bug in oo upstream about this and I reckon there's not much to be done until the bug is sorted out. Have you tried LD_PRELOADing older libfreetype6 library when launching ooffice btw? There's a bug In DBTS in which few people confirm that this workaround actually works.

Thanks for your insightful post on the other thread btw.

Yeah, LD_PRELOADing works. In Feisty, it's unnecessary, since they've already built oo.org against the 2.1.10 libraries. I could never find any other source that could spell this problem out straight forwardly, so I'm hoping that people will come across my post either through the forums and/or through Google so they don't have to go through all the trouble I did to find this out.

I should also thank you for hosting the Turner libs. Another fine example of the Ubuntu philosophy at work :)

---

### Post by mindtrick on 2007-05-29
Hi I'm a newbie, 
I've been using these packages for a time, just now an update came with the Ubuntu auto updater, which advises me to update the "libcairo2" package. What should I do?

---

### Post by mlind on 2007-05-30
> **mindtrick said:**
> Hi I'm a newbie, 
I've been using these packages for a time, just now an update came with the Ubuntu auto updater, which advises me to update the "libcairo2" package. What should I do?

You can safely update. Newest patched **libcairo2** version is 1.4.6-1.1~turner1.

---

### Post by mindtrick on 2007-05-30
Oh, thanks :)

---

### Post by professor76 on 2007-05-31
I installed this latest update to cairo, and have noticed that fonts ( I use true-type) blurred somewhat.

Any idea, if this is intended ?

Thanks

---

### Post by skip27 on 2007-05-31
> **professor76 said:**
> I installed this latest update to cairo, and have noticed that fonts ( I use true-type) blurred somewhat.

Any idea, if this is intended ?

Thanks

Could you post a screenshot? In all likelihood, this is the intended effect. If you are unsatisfied, try adjusting the font settings (under the control panel). More specifically, adjust the levels of hinting (slight/medium/full) to see if you find something to your liking. Additionally, the fonts that you use will also have an effect. For instance, if you use Arial or Tahoma, notice how the number '2' renders under LCD subpixel rendering with full hinting. The body of the number is a bit faint, isn't it? If you reduce the hinting down to slight, however, the problem is fixed. Additionally, you'll notice that the shaping of the Arial characters is MUCH improved with 'slight' hinting. Furthermore, slight hinting is mandatory if you decide to use the Segoe UI from Office 2007/Vista; using medium or full hinting will unnaturally bolden the characters.

---

### Post by Echow on 2007-06-02
Hey all. I've just discovered a strange problem. 
These instructions are great btw, got me good fonts. However, I ran into a major problem with displaying Chinese (and Japanese) in the titlebar (didn't matter what program). The screen would flicker multiple times, then stop and I would be left with all windows displayed except with no window borders (titlebar etc). The only way to get them back was to make sure the offending webpage/program was closed, and then enable+disable desktopeffects (which somehow resets the window border program i think). Now that I've reverted to the (admittedly much uglier) original libs the problem is gone. Does anyone have any ideas on how to rectify this problem so that I can use these newer libs?
Thanks,
Ed
Edit: Ok after a bit more testing I've discovered that the problem only seems to occur when I choose a bold font for the window titles under system>preferences>font. Strangely enough bold+oblique works, oblique works, plain works....hrmmm.
Oh well I can live with that. Should I report this somewhere?

---

### Post by tL0z on 2007-06-02
I'm having some problems:

```
Ign http://www.telemail.fi feisty/fonts Packages                                
Ign http://www.telemail.fi feisty/fonts Sources                          
Err http://www.telemail.fi feisty/fonts Packages   
  404 Not Found
Get:20 http://www.telemail.fi feisty/fonts Sources [957B]
Err http://raof.dyndns.org feisty Release.gpg                                   
  Could not connect to raof.dyndns.org:80 (60.242.199.65), connection timed out
99% [Connecting to raof.dyndns.org (60.242.199.65)]

```

Any ideas?

---

### Post by mlind on 2007-06-02
@ tL0z
If you're using i386 packages, comment out the raof.dyndns.org repository from your sources.list, it seems to be giving "not found" error for you.

---

### Post by tL0z on 2007-06-02
Nop, I have to use AMD64 package as I have an AMD 64 CPU. :)

---

### Post by mlind on 2007-06-02
> **tL0z said:**
> Nop, I have to use AMD64 package as I have an AMD 64 CPU. :)

I can't help you then as I don't maintain the 64bit packages.

---

### Post by Echow on 2007-06-03
@ tL0z
Use the repositories listed at [http://ubuntu.moshen.de/dists/feisty/experimental/](http://ubuntu.moshen.de/dists/feisty/experimental/)
deb [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental
deb-src [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty experimental
Don't forget to add the key. Chuck this in terminal.
wget [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg) -O- | sudo apt-key add -

---

### Post by tL0z on 2007-06-03
I've added the repositories to the sources file and the key, but I got the following error when I did *sudo aptitude update*:

> W: GPG error: [http://ubuntu.moshen.de](http://ubuntu.moshen.de) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC0A1CC62F306651
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems


---

### Post by RAOF on 2007-06-03
I **am** the maintainer of the AMD64 repositories.  The warning above is because you haven't imported the repository's GPG key into your apt keyring.

The reason why raof.dyndns.org is down is because I've moved, and still haven't got internet access.  Oh, and it's now cooperteam.net, as in my sig.  Use the moshen mirror, as it doesn't depend on my internet connection :).

---

### Post by Echow on 2007-06-04
It shold work if you put this in the terminal then restart synaptic/aptitude...

wget [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg) -O- | sudo apt-key add -

I'm not sure what else could be the problem

---

### Post by tL0z on 2007-06-04
Hm, I didn't know I had to insert my password after the key command (didn't notice the sudo). Thanks guys, the font rendering is much better. :)

By the way, how do I restart the X-Server? I had to reboot.

---

### Post by mlind on 2007-06-04
> **tL0z said:**
> Hm, I didn't know I had to insert my password after the key command (didn't notice the sudo). Thanks guys, the font rendering is much better. :)

By the way, how do I restart the X-Server? I had to reboot.

If you're logged in to x session, just log out and press CTRL+ALT+Backspace
or from terminal
```

sudo invoke-rc.d gdm restart

```

---

### Post by aaronw_1986 on 2007-06-04
could this font thing slow down my computer?  I did it last night, and it was working great.  Today when I turned on my comp, it is running really slow.  Any clue why?

---

### Post by mlind on 2007-06-05
> **aaronw_1986 said:**
> could this font thing slow down my computer?  I did it last night, and it was working great.  Today when I turned on my comp, it is running really slow.  Any clue why?

I guess everything is possible, but this is the first time I've heard something like this. Have you tried reverting to the default packages yet and see if the problem persists?

---

### Post by aaronw_1986 on 2007-06-05
I wasn't sure how to revert the packages.  However, I think the problem was fixed now.  It was either the fact that I hadn't enabled hyperthreading, and something with that was slowing it donw, or it was just a fluke for a but.  Seems to be running fine now.

---

### Post by klerfayt on 2007-06-05
first of all - I'm very grateful for repository that allows me to enable sub-pixel rendering for fonts and now the kde specific question:
in kcontrol user can enable/disable sub-pixel hinting at will, even if fontconfig was configured to always use sub-pixel hinting - I want to know what sub-pixel hinting does kcontrol enable, does it use "native" as was told to fontconfig or it uses "auto" (overriding fontconfig settings) + also what happens to forbidden bitmapped fonts - will they be enabled or kcontrol can't mess up fontconfig settings for "hinting" style (native/auto) and bitmapped fonts (enabled/disabled)?

---

### Post by tperica on 2007-06-14
Greetings all,
Fonts are looking great. 
The problem i have is with FIrefox, but not with all web pages, just specific ones. I believe it's part of Firefox problem described[ [COLOR="Red"]here [/COLOR]]("http://www.mozilla.org/unix/customizing.html#fonts")
Does anybody have a solution for this particular problem?


cheers
tomislav

---

### Post by John Doe on 2007-06-17
> **tperica said:**
> Greetings all,
Fonts are looking great. 
The problem i have is with FIrefox, but not with all web pages, just specific ones. I believe it's part of Firefox problem described[ [COLOR="Red"]here [/COLOR]]("http://www.mozilla.org/unix/customizing.html#fonts")
Does anybody have a solution for this particular problem?


cheers
tomislav

Is your problem related to the one I have when viewing a site like this (with subpixel smoothing enabled) ?
[http://john.jubjubs.net/2007/06/14/a-pictures-worth-100m-users/](http://john.jubjubs.net/2007/06/14/a-pictures-worth-100m-users/)

The color of the text below "A Picture’s Worth 100M Users" is supposed to be white, yet, for me (with subpixel smoothing enabled), the text appears in a range/mixture of other colors.  If I turn off subpixel smoothing, the color of the text on that site changes back to white.

---

### Post by screaminj3sus on 2007-06-17
> **John Doe said:**
> Is your problem related to the one I have when viewing a site like this (with subpixel smoothing enabled) ?
[http://john.jubjubs.net/2007/06/14/a-pictures-worth-100m-users/](http://john.jubjubs.net/2007/06/14/a-pictures-worth-100m-users/)

The color of the text below "A Picture’s Worth 100M Users" is supposed to be white, yet, for me (with subpixel smoothing enabled), the text appears in a range/mixture of other colors.  If I turn off subpixel smoothing, the color of the text on that site changes back to white.

Looks fine here, I can't seem to reproduce what you are describing.

---

### Post by tperica on 2007-06-18
Yes, it's looks fine with me too. But pages like this: [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts")

---

### Post by Major_Kong on 2007-06-22
I'm running Ubuntu 7.04 AMD64, and i'm having a problem with the patched libraries.

Whenever i opened any files or websites with a japanese charset (non utf-8 ) - e.g.: [http://homepage3.nifty.com/blacksword/](http://homepage3.nifty.com/blacksword/) - the window manager crashed. After i downgraded to the ubuntu packages the problem disappeared. 

Any sugestions to another solution besides downgrading?


EDIT: Can anyone confirm the problem ?

EDIT2: Wrong link.

---

### Post by Major_Kong on 2007-06-23
No workarounds ?

---

### Post by mlind on 2007-06-23
> **Major_Kong said:**
> No workarounds ?

I have no idea about amd64 packages. I'd try to recompile packages for your architechture from the source packages (from i386 repository).

---

### Post by Major_Kong on 2007-06-23
I'll try that, but i wished somebody with the amd64 packages would confirm the problem...

---

### Post by Major_Kong on 2007-06-25
So, in the 32-bit packages there is no such problem ?

---

### Post by mlind on 2007-06-25
> **Major_Kong said:**
> I'll try that, but i wished somebody with the amd64 packages would confirm the problem...

I tried accessing the url you provided and no abnormal behavior using firefox and the patched libraries on i386. Could you try rebuilding the 3 libraries from source packages (get the sources from i386 repository) and confirm if the problem persists? If you need assistance, just send a pm.

---

### Post by Major_Kong on 2007-06-25
Recompiled from source ( [http://www.telemail.fi/mlind/ubuntu/pool/fonts/](http://www.telemail.fi/mlind/ubuntu/pool/fonts/) ), seems to be working now. 

PS: I gave the wrong link earlier. Already edited it to the right one ( [http://homepage3.nifty.com/blacksword/](http://homepage3.nifty.com/blacksword/) )

EDIT: Something i didn't notice earlier, the packages in the moshen repo are of an earlier version of the patched libraries.

EDIT2: [https://bugs.beta.launchpad.net/ubuntu/+bug/104710](https://bugs.beta.launchpad.net/ubuntu/+bug/104710) - Related ?

---

### Post by mlind on 2007-06-25
> **Major_Kong said:**
> Recompiled from source ( [http://www.telemail.fi/mlind/ubuntu/pool/fonts/](http://www.telemail.fi/mlind/ubuntu/pool/fonts/) ), seems to be working now. 

PS: I gave the wrong link earlier. Already edited it to the right one ( [http://homepage3.nifty.com/blacksword/](http://homepage3.nifty.com/blacksword/) )

EDIT: Something i didn't notice earlier, the packages in the moshen repo are of an earlier version of the patched libraries.

EDIT2: [https://bugs.beta.launchpad.net/ubuntu/+bug/104710](https://bugs.beta.launchpad.net/ubuntu/+bug/104710) - Related ?

yeah, I have no control over moshen repo, just the i386 one, sorry. By looking that backtrace it seems that freetype is causing the crash. Bug shouldn't be reported in Ubuntu bugtracker when you're using un-official packages though.

---

### Post by Major_Kong on 2007-06-25
The guy probably didn't know where the problem was.

Well, thx for the help. 

Maybe i'll email the repo's maintainer about the problem...

---

### Post by Imrahil on 2007-06-26
> **klerfayt said:**
> first of all - I'm very grateful for repository that allows me to enable sub-pixel rendering for fonts and now the kde specific question:
in kcontrol user can enable/disable sub-pixel hinting at will, even if fontconfig was configured to always use sub-pixel hinting - I want to know what sub-pixel hinting does kcontrol enable, does it use "native" as was told to fontconfig or it uses "auto" (overriding fontconfig settings) + also what happens to forbidden bitmapped fonts - will they be enabled or kcontrol can't mess up fontconfig settings for "hinting" style (native/auto) and bitmapped fonts (enabled/disabled)?

OK I can field this one. In kcontrol, when you set sub-pixel hinting, kde will create a .fonts.conf. This will set antialias = true and hinting = true. hintstyle and rgba will be set accordingly. Now this will not override the fontconfig setting so if you chose native, your fonts will still be using native rendering. Fontconfig will automatically choose autohinter if you set your hintstyle to hintslight. If you wish to force the use of the autohinter, enter:

```

<match target="font" >
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
```

The bitmapped font issue is nearly irrelevant. Assuming you are using programs that use Xft, it will never come up. 

Hope this helps.

---

### Post by EDzior on 2007-06-29
Hi, i'm trying to apply the David Turner's patch to libcairo-1.4.8 from debian unstable repository but it looks like this patch doesn't work anymore with this version of cairo. Is there any chance that you have some workaround for this or maybe a modified patch?

Regards

---

### Post by EDzior on 2007-06-29
Ok, i've found a solution for this on Arch forum. PLD developers made a modified David Turner's patch for cairo-1.4.8. To cleanly build a package there is also needed a second patch.
Below there are this two patches modified for debian:

---

### Post by mlind on 2007-06-29
> **EDzior said:**
> Ok, i've found a solution for this on Arch forum. PLD developers made a modified David Turner's patch for cairo-1.4.8. To cleanly build a package there is also needed a second patch.
Below there are this two patches modified for debian:

yes, I previously modified the patch (looks familiar) for gutsy's libcairo2 and included in gutsy's font packages. feisty still has libcairo 1.4.6.
I'm curious about the second patch though as I didn't need it to get the package compile. What does it actually improve?

/edit
no matter, the second patch fixes issue only in libcairo 1.4.8.
debian unstable/gutsy already has 1.4.10 with this issue fixed.

---

### Post by xen on 2007-07-01
Last time I checked, the amd64 repositories weren't responding. Anyone else experienced this?

---

### Post by RAOF on 2007-07-01
> **xen said:**
> Last time I checked, the amd64 repositories weren't responding. Anyone else experienced this?

The cooperteam.net repository should be back up, and the ubuntu.moshen.de repository should never have gone down :).

I'll build the newer packages for those repositories soon.

---

### Post by drably on 2007-07-08
I am a laptop user with a resolution of 1440x900 and I'm using KDE as my desktop with the default fiesty settings + a couple of adjustments: DPI set to 96, and anti-aliasing set to system settings (however relevant this may be if at any)

From my perspective, hopefully these patches never become accepted as standard. Maybe people do not know how to pick proper fonts, or adjust their display settings correctly, since I do not have any of the problems any of you people have with any applications or web pages.

However, I do know when I installed these so called 'fixes' for this non-existant problem that I do not experience, but all of you apparently do, my fonts looked horrible. Just trying to read various web pages with different design elements which was formerly tolerable became annoying and unbearable. Fonts in flash were pixelated and overly out of proportion. Text in web pages that was suppose to be bold ended up being 5x more bold than usual, causing disproportional unalignment within web pages etc. No matter how I adjusted my settings with every logical setting, I could not fix the new found problems caused by installing these packages.

After reading 23 pages of nothing but problems and complains, I should have known better than to even see what benefits could come from this. Now I know there are none worthwhile. I am happy to say I uninstalled this so called solution, and reverted back to my original settings, and I could not be happier.

My advice: stay away

---

### Post by bhaagensen on 2007-07-08
> **drably said:**
> My advice: stay away

I think that advice is a bit undifferientiated. Yes there are problems, which one can find lots of info about in this thread. Nevertheless subpixel rendering is *the best way* of rendering text on LCD's. And for those who are interested in using this technology these packages are interesting. For me and many others they make fonts look better 'in most' cases.

So I think it would be more fair to say that these packages provide better looking fonts on LCD's, but the technology is new and hence not supported by all applications, notably fonts in ooffice and firefox may sometimes look worse than before. Fixes for some of these problems are discussed in this thread.

Bjørn

---

### Post by hugmenot on 2007-07-08
Hah, my fonts look better in /all/ cases. No offense, really.
BTW I just had a good read, with a nice introductory quote:

> This &#8220;fanboyism&#8221; is reckless. It is equivalent to saying &#8220;I don't care about the resolution, I just want to have my 96 DPI for ever, with the Windows-style text, and so, I vote for stopping the progress.&#8221; Is that clever?

[http://antigrain.com/research/font_rasterization/index.html](http://antigrain.com/research/font_rasterization/index.html)

---

### Post by mlind on 2007-07-12
> **drably said:**
> I am a laptop user with a resolution of 1440x900 and I'm using KDE as my desktop with the default fiesty settings + a couple of adjustments: DPI set to 96, and anti-aliasing set to system settings (however relevant this may be if at any)

From my perspective, hopefully these patches never become accepted as standard. Maybe people do not know how to pick proper fonts, or adjust their display settings correctly, since I do not have any of the problems any of you people have with any applications or web pages.

However, I do know when I installed these so called 'fixes' for this non-existant problem that I do not experience, but all of you apparently do, my fonts looked horrible. Just trying to read various web pages with different design elements which was formerly tolerable became annoying and unbearable. Fonts in flash were pixelated and overly out of proportion. Text in web pages that was suppose to be bold ended up being 5x more bold than usual, causing disproportional unalignment within web pages etc. No matter how I adjusted my settings with every logical setting, I could not fix the new found problems caused by installing these packages.

After reading 23 pages of nothing but problems and complains, I should have known better than to even see what benefits could come from this. Now I know there are none worthwhile. I am happy to say I uninstalled this so called solution, and reverted back to my original settings, and I could not be happier.

My advice: stay away

I can feel your frustration, too bad these weren't no use for you. I wonder what default settings KDE uses for fonts, I have a feeling that most of the odd font rendering posts are from KDE users. I accidentally compiled freetype without  **FT_CONFIG_OPTION_SUBPIXEL_RENDERING** enabled and results were horrible, like in few screenshots posted earlier (libcairo2 and xft were patched).

Do you use customized ~/.fonts.conf by the way?

---

### Post by Emblem Parade on 2007-07-12
Some of the messages here piss me off.

People should use a nicer tone when complaining about this package. Calling it "worthless" just because it doesn't work for you is a bit extreme, don't you think? And inducing from your experience that nobody else would want it, is also a bit extreme, don't you think? If you feel a burning desire to share your experience, just say that it didn't work for you, and please refrain from judgment.

It might also be nice to do look more closely at what it is, exactly, that you're installing here, what the legal and technical limitations are, and who is involved. There are very good reasons for this not being in the Ubuntu repositories.

David Turner was one of the main developers of FreeType, the most popular font rendering engine in the free software world. We owe him a lot. During development, he also worked on adding support for sub-pixel rendering, a rather ingenious algorithm, which uses the technical "limitation" in making color for LCD displays to actually increase the apparent resolution for black lines. Perfect, of course, for fonts. Unfortunately, this exact use is patented by Microsoft. Apple does use it to produce its crisp LCD fonts, but it pays Microsoft licensing fees for this. (And for quite a few other things, too!) Since very few free operating systems are in the position to pay such licensing fees (and there are obvious ideological objections to doing so), there are only a few, commercial free operating systems that have it.

Obviously, when David Turner found out about the patent, he was disheartened, and stopped development. If the legal issues are solved (unlikely), this has the potential to make free software desktops look just as good as Mac OS.

Turner's unfinished code is still there in FreeType, disabled. What mlind did was enable it, rebuild it, adapt the higher-lever font packages (such as Cairo) to make use of this feature, and package it nicely in a repository for us Ubuntu users. He's also working on debugging it and tuning it through feedback he gets on this thread. Because the legality of this is at issue, this is done in low profile, buried deep here within the Ubuntu forums, anonymously.

What you're getting here is unfinished, mostly untested software, provided for you at some risk. It obviously does not work well for all setups. For my setup, it did wonders, and I can't imagine Ubuntu without it. There are problems in Firefox and OpenOffice, but otherwise it's made my many hours in front of an LCD screen bearable.

I'd like to thank everyone involved in making this repository.

---

### Post by hugmenot on 2007-07-12
A few substantial corrections.

- Turner still is the main developer of FreeType, he just has a day job and lacks the resources to push the next big font revolution into all corners of the free desktop.
- Apples fonts are not crisp, far from it. And intentionally at that. Also they don&#8217;t pay Microsoft for SR, they have a mutual exchange. MS uses Apples hinting patent for instance.
- When Turner had researched the patents he made the step to not enable them in default builds to not bring unsuspecting developers into a vulnerable position. Not after making an effort to bring SR in FreeType to a quality that rivals all other implementations. This part of the revolution can be considered complete. It has been part of the stable source tarball since months. What he is not ready to do now is work with all sorts of text-layout downstream developers to implement advanced stuff like subpixel positioning, which looks absolutely splendid in the ftdiff FreeType demo.
- We&#8217;re not doing this intentionally low-profile, we&#8217;re doing this because Ubuntu cannot include it to not make itself liable to infringement of MS patents. As lone users compiling stuff not much harm is done. It&#8217;s a pity about the lack of coverage we can get, but anyhow.
- About legality, enabling the bytecode interpreter by default and not the autohinter is an obvious infringement on Ubuntu&#8217;s side. Those patent isues have been known for a long time. Both BCI and SR should not be compiled to be in the clear.

About your comments on mlinds work, those are true; he is a tireless worker for the good cause. =D>

EDIT: some of my points were drawn from two replies of David to the article I mentioned above, they are interesting
1. [http://article.gmane.org/gmane.comp.fonts.freetype.user/2370](http://article.gmane.org/gmane.comp.fonts.freetype.user/2370)
2. [http://article.gmane.org/gmane.comp.fonts.freetype.user/2371](http://article.gmane.org/gmane.comp.fonts.freetype.user/2371)

---

### Post by Emblem Parade on 2007-07-13
Thanks, HugMeNot! I didn't think my points contradicted any of yours, except that, well:

1. The "crispiness" of Mac OS's fonts is a matter of personal preference (just like not everybody on this list likes the enhanced FreeType package). I happen to like them. :)

2. While Turner completed his dev work, it's necessary to do work throughout the various operating systems and applications, and also a lot of testing, as you mentioned. Sometimes this takes much more work than the basic dev work, and that's especially true with fundamental technology like this. It can take years to get all the issues worked out. Turner doesn't have to do this specifically by himself, but it's still a lot more work that needs to be done. So, I don't think we should call it complete, yet. And with the legal issues, it's kinda hard to get everybody together and do this.

3. It took me months using Ubuntu until I found these packages! I would consider this to be quite low profile! If you want to raise the profile, try creating a web site, or even a HOWTO on the Ubuntu wiki. As it stands, I'm not sure I would support that move, because it could see this effort squashed. I know you don't want things to be this way, and neither does anyone. Hopefully, one day, patent laws will be the ones squashed. In the meantime, we are the true heroes. :)

4. I consider mutual exchange of patents to be a kind of payment.

> **hugmenot said:**
> A few substantial corrections.

- Turner still is the main developer of FreeType, he just has a day job and lacks the resources to push the next big font revolution into all corners of the free desktop.
- Apples fonts are not crisp, far from it. And intentionally at that. Also they don’t pay Microsoft for SR, they have a mutual exchange. MS uses Apples hinting patent for instance.
- When Turner had researched the patents he made the step to not enable them in default builds to not bring unsuspecting developers into a vulnerable position. Not after making an effort to bring SR in FreeType to a quality that rivals all other implementations. This part of the revolution can be considered complete. It has been part of the stable source tarball since months. What he is not ready to do now is work with all sorts of text-layout downstream developers to implement advanced stuff like subpixel positioning, which looks absolutely splendid in the ftdiff FreeType demo.
- We’re not doing this intentionally low-profile, we’re doing this because Ubuntu cannot include it to not make itself liable to infringement of MS patents. As lone users compiling stuff not much harm is done. It’s a pity about the lack of coverage we can get, but anyhow.
- About legality, enabling the bytecode interpreter by default and not the autohinter is an obvious infringement on Ubuntu’s side. Those patent isues have been known for a long time. Both BCI and SR should not be compiled to be in the clear.

About your comments on mlinds work, those are true; he is a tireless worker for the good cause. =D>

EDIT: some of my points were drawn from two replies of David to the article I mentioned above, they are interesting
1. [http://article.gmane.org/gmane.comp.fonts.freetype.user/2370](http://article.gmane.org/gmane.comp.fonts.freetype.user/2370)
2. [http://article.gmane.org/gmane.comp.fonts.freetype.user/2371](http://article.gmane.org/gmane.comp.fonts.freetype.user/2371)

---

### Post by nphx on 2007-07-18
WOW big difference. Very smooth, this is awesome! Thank you so much for this.

---

### Post by amoore on 2007-07-19
Great how to!!! I've finally got good looking fonts!!!!

---

### Post by kadath on 2007-07-19
The people bitching in this thread that their fonts look horrible after installing the patched debs either:

A) Are too accustomed to Windows' horrid ClearType font rendering (or are not having ClearType on *at all*);

or

B) Don't know how to properly choose and configure their fonts.

Quite frankly, using these patches on my system, my fonts look far smoother and render better than fonts do on my Windows partition with ClearType enabled, yet look a bit sharper than OS X's slightly blurry font rendering.

Of course, it's also a matter of personal taste. But the people complaining that the debs mlind is providing are "trash" need to simply uninstall them and continue using whatever config they prefer. I appreciate mlind's work in maintaining these packages and hope he continues to.

---

### Post by Tamale on 2007-07-19
> **Mlehliw said:**
> Here are my before and after pics, I used Native, Automatic, No bitmapped fonts, like the OP. Maybe I did something wrong but I like the original fonts better, the new ones are too "fuzzy" for me.

The left picture is the before picture, and on the right is the after picture by the way.

My fonts look like his "after" pic after my new install of feisty... I'd like them to look like the "before" like they did on my edgy install.. what can I do?

---

### Post by Ted Nancy on 2007-07-20
Wow. I was reading through the thread, thinking really why do I need this? Why hack away at my system when my fonts already look great? But seeing how easy it was to undo I decided, meh, what the 'ell.

Wow. This is amazing. I never realized how good fonts could look. 

Thanks to everyone involved for this.

---

### Post by rohandhruva on 2007-07-20
Hi .. The fonts are looking absolutely amazing now. Thanks for all the work, the patches, and the packages. Please keep it you ! :)

---

### Post by The Pinny Parlour on 2007-07-20
> **mlind said:**
> For reference see **hugmenot**'s related [[COLOR="Sienna"]Edgy thread[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=235526").

Patched libraries are built against **freetype** 2.3.x (not currently in feisty) and include [COLOR="Blue"]David Turner[/COLOR]'s subpixel rendering [patches]("http://david.freetype.org/lcd/").
```

deb http://www.telemail.fi/mlind/ubuntu feisty fonts
deb-src http://www.telemail.fi/mlind/ubuntu feisty fonts

```
**[COLOR="Blue"][edit][/COLOR]**
for **amd64** binaries use [RAOF's repository]("http://ubuntu.moshen.de/dists/feisty/experimental")
```

deb http://raof.dyndns.org/falcon feisty experimental
deb-src http://raof.dyndns.org/falcon feisty experimental

```

[COLOR="Silver"]Alternative repository, for experimental builds only.[/COLOR]
```

deb http://www.telemail.fi/mlind/ubuntu feisty experimental
deb-src http://www.telemail.fi/mlind/ubuntu feisty experimental

```


**Notes**
[LIST]
[*]To install the packages
```

sudo aptitude update
sudo aptitude install libfreetype6 libcairo2 libxft2

```
[*]After the install, you may want reconfigure font settings. I'm currently using Feisty defaults (Native, **Always**, No bitmapped fonts) myself.
```

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

```
[*]If you get errors about **missing gpg key**
```

wget http://www.telemail.fi/mlind/ubuntu/937215FF.gpg -O- | **sudo** apt-key add -

```
(or alternatively)
```

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

```
[*]GPG key to RAOF's repository (amd64 packages)
```

wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -

```
[*]If you later decide to go back to Ubuntu packages, you must downgrade **all** three installed packages
[*]You'll probably need to restart X-server after installing the packages to see the changes apply
[/LIST]

I was looking forward to this but it doesn't work. :(  bash: deb: command not found

---

### Post by benjaminzsj on 2007-07-20
> **The Pinny Parlour said:**
> I was looking forward to this but it doesn't work. :(  bash: deb: command not found
Those lines starting with "deb" are not supposed to be typed in your console, they should be added to the file "/etc/apt/sources.list".

---

### Post by The Pinny Parlour on 2007-07-20
> **benjaminzsj said:**
> Those lines starting with "deb" are not supposed to be typed in your console, they should be added to the file "/etc/apt/sources.list".

Ok thanks.  I'm still trying to work out why there in CODE tags then?

---

### Post by misfitpierce on 2007-07-20
Same... Nice

---

### Post by hugmenot on 2007-07-20
> **The Pinny Parlour said:**
> Ok thanks.  I'm still trying to work out why there in CODE tags then?

Because CODE is a misnomer for "use typewriter font".

---

### Post by The Pinny Parlour on 2007-07-20
Completed it and I notice ZERO effect on my fonts.  I must of had them set up properly to start with.

---

### Post by The Pinny Parlour on 2007-07-20
BTW how does one Downgrade all 3 packages?

---

### Post by Jamesbowden on 2007-07-20
I don't like the way these packages make the font's look on my screen, so I tried to remove and downgrade the packages, however apparently almost everything in my GUI depends on them =/.

I did sudo aptitude remove libfreetype6 libcairo2 libxft2 and aptitude tells me in is going to download some of the packages, but still no change.

how can I fix this?

---

### Post by The Pinny Parlour on 2007-07-20
Yep I'd like to know how to rid the system of em myself.

---

### Post by ThrobbingBrain66 on 2007-07-20
Comment out (or delete) the repos from your sources.list file.
```
sudo apt-get update
```
ater that
```
sudo apt-get install libfreetype6/feisty libxft2/feisty libcairo2/feisty
```

---

### Post by w31rd0 on 2007-07-20
to downgrade you'll need to manually download those (unpatched) packages from official ubuntu repository and install em using "sudo dpkg -i ..."

---

### Post by hugmenot on 2007-07-20
> **The Pinny Parlour said:**
> Completed it and I notice ZERO effect on my fonts.  I must of had them set up properly to start with.

Yes, that's likely.

---

### Post by jackhynes on 2007-07-20
> **The Pinny Parlour said:**
> Completed it and I notice ZERO effect on my fonts.  I must of had them set up properly to start with.
You did restart X right?

---

### Post by Mark_in_Hollywood on 2007-07-20
Please pardon my ignorance, but will this work with Gutsy, if i change the repository identity?

---

### Post by hugmenot on 2007-07-20
Yes, just replace feisty with gutsy.

---

### Post by mlind on 2007-07-20
> **Jamesbowden said:**
> I don't like the way these packages make the font's look on my screen, so I tried to remove and downgrade the packages, however apparently almost everything in my GUI depends on them =/.

I did sudo aptitude remove libfreetype6 libcairo2 libxft2 and aptitude tells me in is going to download some of the packages, but still no change.

how can I fix this?

> **The Pinny Parlour said:**
> Yep I'd like to know how to rid the system of em myself.

hiya guys,
as others pointed out already, there's probably something wrong how your font settings are if things don't look alright with the patched libs. If you could elaborate bit more, are either of you using CRT display and/or KDE desktop?

If you want to get rid of the packages do as **ThrobbingBrain66** said earlier.

---

### Post by Tamale on 2007-07-20
mlind:

I'll try my best to explain the differences I'm seeing and sincerely hope you can help me.. I'm getting a headache at times looking at these fonts on feisty.. with or without your patch.. and I can't get a decent looking set of fonts for firefox after playing with so many different how-tos, font settings, blah blah etc etc..  that I'm going crazy!

I'm including a couple links to screenshots to try to help illustrate my problem..

here is a screenshot from my edgy install where everything looks perfect imo:
[http://www.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png](http://www.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png)

and here is the very best I've been able to do so far in Feisty.. currently I'm using the new packages referenced in this thread:
[http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeisty.png](http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeisty.png)

the biggest and easiest place to see a difference is in the capital "N"s in the font details (in the word "None" under Smoothing).  Notice how in edgy, the diagonal line is just as thin visually as the vertical lines, but in feisty the diagonal line is nearly twice as thick.  the lowercase x is also much thicker looking.

also, notice now in the terminal how the 'o' in joshua doesn't even look like it's centered properly in feisty..

more frustrating than either of these two complaints though is how firefox renders the difference between bold and non-bolded texts.. look at "Google Calendar" in the edgy shot, and then one of the bolded store names in the feisty shot of firefox in the webpage.. they're huge compared to their non-bolded counterparts!  it makes most pages look downright awful and I can't find ANYWAY to disable that short of using some awful poorly created font

i realize it looks like i'm complaining about really minor things, but they're very noticeable to me because i've been using these beautiful dapper drake/edgy eft bitstream vera sans fonts for so long my eyes have grown extremely accustomed to them and i just want those again in feisty... seems like if they worked once before i should be able to get them again, right?

if someone could walk me through things to try on irc, i'd be more than willing to sit and work through things.. i'm typically in #ubuntu-effects and i've got my edgy install on another partition so i can look at things and even boot into it if need be to check settings..

---

### Post by Shpongled303 on 2007-07-21
Thanks for this. :) Found the link to this thread through lifehacker.com news.

I love when you guys write these guides that are so simple for us newbies to understand. :D

Much appreciated,
Shpongled

---

### Post by hugmenot on 2007-07-21
> **Tamale said:**
> 
here is a screenshot from my edgy install where everything looks perfect imo:
[http://www.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png](http://www.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png)

and here is the very best I've been able to do so far in Feisty.. currently I'm using the new packages referenced in this thread:
[http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeisty.png](http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeisty.png)


You do not use the packages from this thread. The vertical stems are thin precisely because you don't.They are snapped, if you used mlinds packages you would see color filtering on stems as well, not only in the bowls/corners. That&#8217;s the property of the poor subpixel setting in the default packages. Also you use "full hinting" when you might get better shapes with slight. But beware, stems will et stronger. For some that means better optics, for some "less crispness" whatever they mean with that.

If you do have the packages installed, I guess you cluttered your system with all kinds of customizations of fonts.conf and whatnot. Try to get rid of those.

---

### Post by Tamale on 2007-07-21
> **hugmenot said:**
> You do not use the packages from this thread. The vertical stems are thin precisely because you don't.They are snapped, if you used mlinds packages you would see color filtering on stems as well, not only in the bowls/corners. That’s the property of the poor subpixel setting in the default packages. Also you use "full hinting" when you might get better shapes with slight. But beware, stems will et stronger. For some that means better optics, for some "less crispness" whatever they mean with that.

If you do have the packages installed, I guess you cluttered your system with all kinds of customizations of fonts.conf and whatnot. Try to get rid of those.

Well, if I followed the instructions in this thread and got what you see in these screenshots and they're not "right", then could you help me figure out what might causing problems?  I've removed my .fonts.conf file already and it didn't change anything.

---

### Post by hugmenot on 2007-07-21
> **Tamale said:**
> Well, if I followed the instructions in this thread and got what you see in these screenshots and they're not "right", then could you help me figure out what might causing problems?  I've removed my .fonts.conf file already and it didn't change anything.
What does 
```
apt-cache policy libfreetype6 libcairo2 libxft2
```
give as output?

If you switch to "Slight" hinting, how does it look?

---

### Post by Tamale on 2007-07-21
> **hugmenot said:**
> What does 
```
apt-cache policy libfreetype6 libcairo2 libxft2
```
give as output?

If you switch to "Slight" hinting, how does it look?
```

$ apt-cache policy libfreetype6 libcairo2 libxft2
libfreetype6:
  Installed: 2.3.5-1mlind1~feisty0.1
  Candidate: 2.3.5-1mlind1~feisty0.1
  Version table:
 *** 2.3.5-1mlind1~feisty0.1 0
        500 http://www.telemail.fi feisty/fonts Packages
        100 /var/lib/dpkg/status
     2.2.1-5ubuntu1.1 0
        500 http://security.ubuntu.com feisty-security/main Packages
     2.2.1-5ubuntu1 0
        500 cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages
        500 http://us.archive.ubuntu.com feisty/main Packages
libcairo2:
  Installed: 1.4.10-1turner3~feisty0.1
  Candidate: 1.4.10-1turner3~feisty0.1
  Version table:
 *** 1.4.10-1turner3~feisty0.1 0
        500 http://www.telemail.fi feisty/fonts Packages
        100 /var/lib/dpkg/status
     1.4.2-0ubuntu1 0
        500 cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages
        500 http://us.archive.ubuntu.com feisty/main Packages
libxft2:
  Installed: 2.1.12-2turner2~feisty0.1
  Candidate: 2.1.12-2turner2~feisty0.1
  Version table:
 *** 2.1.12-2turner2~feisty0.1 0
        500 http://www.telemail.fi feisty/fonts Packages
        100 /var/lib/dpkg/status
     2.1.12-1 0
        500 cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Packages
        500 http://us.archive.ubuntu.com feisty/main Packages

```

this is how it looks with slight:  (even worse!) :(
[img]http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeistySlight.png[/img]
again, the difference between bold and regular is just so strong.. it wasn't like that in edgy

---

### Post by Slip_A2 on 2007-07-21
All the system was with the effect, but firefox not, sees the image. 
	
All the system was with the effect, but firefox not, sees the image. It sees the bar of menus of firefox, still is compared milling if of ubuntu (above). 

They forgive my English, but I am Brazilian and am using the Google Translante.

---

### Post by hugmenot on 2007-07-22
> **Tamale said:**
> 
this is how it looks with slight:  (even worse!) :(
[img]http://www.uic.edu/~jbuss2/pics/ubuntu/fontsFeistySlight.png[/img]
again, the difference between bold and regular is just so strong.. it wasn't like that in edgy


Alright so far for the packages. Now, one thing you can try is enabling hinting for the bold fonts to make them more light (see first post).

EDIT: I justed realized the fontconfig setting overrides the custom hintstyle.

This should work:```
$ cat .fonts.conf 
<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- If the font is bold, turn off autohinting -->
  <match target="font">
    <test name="weight" compare="more">
      <const>medium</const>
    </test>
    <edit mode="assign" name="autohint">
      <bool>false</bool>
    </edit>
    <edit mode='assign' name='hintstyle'>
      <const>hintfull</const>
    </edit>
  </match>
</fontconfig>

```

---

### Post by Jonq on 2007-07-22
i have added ubuntu.moshen.de repository but when i try to install amd64 debs i get errors in terminal that the objects are not found checked on web and there is no amd 64 debs available :confused:

anyother repositories for AMD64 ?

---

### Post by Tamale on 2007-07-23
> **hugmenot said:**
> Alright so far for the packages. Now, one thing you can try is enabling hinting for the bold fonts to make them more light (see first post).

EDIT: I justed realized the fontconfig setting overrides the custom hintstyle.

This should work:```
$ cat .fonts.conf 
<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- If the font is bold, turn off autohinting -->
  <match target="font">
    <test name="weight" compare="more">
      <const>medium</const>
    </test>
    <edit mode="assign" name="autohint">
      <bool>false</bool>
    </edit>
    <edit mode='assign' name='hintstyle'>
      <const>hintfull</const>
    </edit>
  </match>
</fontconfig>

```

I'm afraid this isn't helping my "bolded font is way too big compared to non-bold fonts" problem.. 

If it helps any in fixing my issues, with some fonts the bolded text is antialiased while the non-bold version of the exact same font isn't... it's this way for all my MS fonts and fonts like Saab and Standard Symbols..

---

### Post by amgeex on 2007-07-24
Anyone knows if there are any other AMD64 repositories available? RAOF's repository is dead, and so its the mirror. I really want to improve the standard fonts, because the actual ones hurt my eyes, its getting annoying.

Thanks in advance,
amgeex

---

### Post by RAOF on 2007-07-24
> **amgeex said:**
> Anyone knows if there are any other AMD64 repositories available? RAOF's repository is dead, and so its the mirror. I really want to improve the standard fonts, because the actual ones hurt my eyes, its getting annoying.

Thanks in advance,
amgeex

Oh, is moshen dead?  That I didn't know.

The cooperteam.net repository should be back up sometime this week hopefully, after a rollback to Feisty :)

---

### Post by amgeex on 2007-07-24
Thanks for the fast reply. Moshen is "alive", but when apt tries to pull the packages it gets a 404 error, so yeah, its dead pretty much. :P

---

### Post by gumjo on 2007-07-26
Hello, is it possible to get a source file for this package so that one can compile this for other distros?

---

### Post by pswartout on 2007-07-27
> **RAOF said:**
> Oh, is moshen dead?  That I didn't know.

The cooperteam.net repository should be back up sometime this week hopefully, after a rollback to Feisty :)

Please don't take too long getting this up and running, I've installed on my i386 feisty laptop install and the difference in appearance is remarkable \\:D/ - I think everyone with feisty AMD64 should also have this available to them :)

BTW - the problem with the ubuntu.moshen.de/ mirror is that it's giving 404 errors on some experimental packages. maybe could be some links missing:confused:

---

### Post by amgeex on 2007-07-27
The Moshen repo is giving 404 on all the packages, not just the experimental ones.

---

### Post by mlind on 2007-07-28
> **gumjo said:**
> Hello, is it possible to get a source file for this package so that one can compile this for other distros?

Add the source repository (mentioned in the first post) to your /etc/apt/sources.list and then use *apt-get source* to grab the source packages.

---

### Post by amgeex on 2007-07-29
> **mlind said:**
> Add the source repository (mentioned in the first post) to your /etc/apt/sources.list and then use *apt-get source* to grab the source packages.

He probably wants to know if there are tarballs with the source code available to compile under any other distribution, not just ubuntu.

Any news about the 64 bit repos? These patches are quite a necessity now... :P

---

### Post by mlind on 2007-07-29
> **amgeex said:**
> He probably wants to know if there are tarballs with the source code available to compile under any other distribution, not just ubuntu.

Any news about the 64 bit repos? These patches are quite a necessity now... :P

In this case, one can do the following
```

cd /tmp
wget http://www.telemail.fi/mlind/ubuntu/pool/fonts/f/freetype/freetype_2.3.5.orig.tar.gz
tar xzvf freetype_2.3.5.orig.tar.gz
cd freetype-2.3.5.orig
wget -O- http://www.telemail.fi/mlind/ubuntu/pool/fonts/f/freetype/freetype_2.3.5-1mlind1.diff.gz | zcat | patch -p1

```

And do the same for other 2 packages. Download the original source package, extract it and apply corresponding .diff.gz.

---

### Post by amgeex on 2007-07-29
Thanks, I will give this a try! :D

---

### Post by amgeex on 2007-07-29
> **mlind said:**
> In this case, one can do the following
```

cd /tmp
wget http://www.telemail.fi/mlind/ubuntu/pool/fonts/f/freetype/freetype_2.3.5.orig.tar.gz
tar xzvf freetype_2.3.5.orig.tar.gz
cd freetype-2.3.5.orig
wget -O- http://www.telemail.fi/mlind/ubuntu/pool/fonts/f/freetype/freetype_2.3.5-1mlind1.diff.gz | zcat | patch -p1

```

And do the same for other 2 packages. Download the original source package, extract it and apply corresponding .diff.gz.

Ok, I've downloaded and patched the required packages, but how do I install them? In the freetype folder I extracted and then patched I do not see any makefiles or anything, but the Cairo and Xft folders do have the normal stuff to do ./configure, make and make install. My guess is that this freetype source must be built with some debian tools, but I don't know how. I'd appreciate if you shed some light on this, thanks! :)

---

### Post by RAOF on 2007-07-29
> **amgeex said:**
> He probably wants to know if there are tarballs with the source code available to compile under any other distribution, not just ubuntu.

Any news about the 64 bit repos? These patches are quite a necessity now... :P

News is: I'm working out how to make falcon 2.0 work.  After that, I should be ready to go.

---

### Post by jayson.rowe on 2007-07-29
can someone send me a PM or an email @ jayson.rowe (at) gmail.com as soon as there is a repo up that has these patches???

I just did a re-install due to getting a new Raptor HDD and wanting my OS on it, and now I'm stuck in fuzzy rainbow font heck!

---

### Post by mlind on 2007-07-30
> **amgeex said:**
> Ok, I've downloaded and patched the required packages, but how do I install them? In the freetype folder I extracted and then patched I do not see any makefiles or anything, but the Cairo and Xft folders do have the normal stuff to do ./configure, make and make install. My guess is that this freetype source must be built with some debian tools, but I don't know how. I'd appreciate if you shed some light on this, thanks! :)

For what distribution are you exactly compiling the packages? Does your distribution offer the freetype >= 2.3.0 source package which you could just patch and rebuild?

Debian/Ubuntu freetype source package is basically the upstream tarballs (freetype, freetype-demos and freetype documentation) with a Makefile (debian/rules) and bunch of (deb)helper related files (other files in debian/ folder). The actual build process among other things, goes through the Makefile rules in order. Take a look in debian/rules file to see what happens (the dh_* stuff is Debian/Ubuntu specific).

So you'll have to manually extract the freetype-2.3.5.tar.bz2 package, apply *.patch files from debian/patches-freetype/ and then ./configure --prefix=/usr CFLAGS="-g -O2 -fno-strict-aliasing" followed by make and make install.

Something like this
```

tar jxvf freetype-2.3.5.tar.bz2
cd freetype-2.3.5
patch -p1 < ../debian/patches-freetype/enable-subpixel-rendering.patch
## maybe apply other patches from the folder too
./configure --prefix=/usr CFLAGS="-g -O2 -fno-strict-aliasing"
make
make install

```
You probably know better what prefix and build flags you want to use, so that was just an example. Hopefully this helps a bit.

---

### Post by amgeex on 2007-07-30
I'm compiling this for ubuntu feisty 64 bit, but I'll wait for RAOF's repository to come up. If it doesn't then I'll give this a go, thanks for the info mate! ;)

---

### Post by bing on 2007-07-30
Hi everybody,

I encountered a bug in Feisty's Openoffice 2.2.0 and decided to uninstall it and do the upgrade to 2.2.1 through the RPM packages on the official website via alien.

I encountered the ugly font problem and tried the approach suggested by mlind in post #140 by extracting the libfreetype6 found in default Feisty. I also tried the 6.3.8 found in Dapper and neither worked to beautify my fonts (although it might have been slightly better).

I use the latest mlind builds for feisty, Autohinter, Force subpixel in fontconfig. I rebuild the font cache. In Gnome, I set Grayscale and None or Slight hinting. I have tried enabling or disabling font aliasing in Openoffice. Despite these settings, the fonts - either Microsoft or Bitstream - are quite ugly (some uglier than others).

Is there something that I am missing?

---

### Post by giorgosts on 2007-07-31
Openoffice installs standalone in the /opt/ directory (or your /home/ directory), without having to mess up with your original installation.

---

### Post by mlind on 2007-07-31
> **amgeex said:**
> I'm compiling this for ubuntu feisty 64 bit, but I'll wait for RAOF's repository to come up. If it doesn't then I'll give this a go, thanks for the info mate! ;)

ah, If you're just using different architecture then download the source packages using apt-get source and use autobuilder like pbuilder/sbuild. Ubuntu wiki contains nice articles how to setup one of these tools. Just remember to build against the patched freetype.

Don't go configuring already debianized packages manually ;)

---

### Post by amgeex on 2007-08-01
Thanks! :) Any word on the repos' status?

---

### Post by mlind on 2007-08-02
> **amgeex said:**
> Thanks! :) Any word on the repos' status?

I'm not sure about amd64 repository, but here's how you can compile your own using pbuilder.
Setup the build environment using this guide [http://ubuntuforums.org/showthread.php?t=206382](http://ubuntuforums.org/showthread.php?t=206382), **but only follow steps 3, 4 and 5**, skip everything else.

Then make sure you have universe repository enabled and the source repository for the font packages, then
```

sudo aptitude install cowdancer pbuilder
sudo cowbuilder --create
mkdir /tmp/fonts
cd /tmp/fonts
apt-get source freetype libcairo2 libxft2
sudo cowbuilder --build freetype_2.3.5-1mlind1~feisty0.1.dsc
sudo cowbuilder --build libcairo_1.4.10-1turner3~feisty0.1.dsc
sudo cowbuilder --build xft_2.1.12-2turner2~feisty0.1.dsc

```

Then install libfreetype6_*.deb, libcairo2_*.deb and libxft2_*.deb binaries from ~/pbuilder/results. Only 3 packages should get installed.


/edit
To speed up the build process vastly, put this in your ~/.pbuilderrc
```

# use gdebi for dependency resolution
PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi

```

---

### Post by xellzhang on 2007-08-02
[COLOR="Blue"]**[It is ok now :)]**[/COLOR]

Hi, I just added:
[COLOR="Blue"]deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts[/COLOR]
to my source.list and ran a update.
Then I tried to upgrade my system but I got:
[COLOR="Red"]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main gnupg 1.4.6-2ubuntu3~feisty1
  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.6-2ubuntu3~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.6-2ubuntu3~feisty1_i386.deb)  404 Not Found [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/COLOR]

I checked "http://archive.ubuntu.com/ubuntu/pool/main/g/gnupg/" and there was no filed called "gnupg_1.4.6-2ubuntu3~feisty1_i386.deb"

Does anyone know about this? How to fix this?

---

### Post by rocketbomb on 2007-08-04
...

---

### Post by dannymichel on 2007-08-04
root@danny-desktop:/tmp/fonts# sudo cowbuilder --build freetype_2.3.5-1mlind1~feisty0.1.dsc
File not found: freetype_2.3.5-1mlind1~feisty0.1.dsc
root@danny-desktop:/tmp/fonts# sudo cowbuilder --build libcairo2_1.4.10-1turner3~feisty0.1.dsc
File not found: libcairo2_1.4.10-1turner3~feisty0.1.dsc
root@danny-desktop:/tmp/fonts# sudo cowbuilder --build libxft2_2.1.12-2turner2~feisty0.1.dsc
File not found: libxft2_2.1.12-2turner2~feisty0.1.dsc
root@danny-desktop:/tmp/fonts# sudo cowbuilder --build freetype_2.3.5-1mlind1~feisty0.1.dsc
File not found: freetype_2.3.5-1mlind1~feisty0.1.dsc
root@danny-desktop:/tmp/fonts# apt-get source freetype libcairo2 libxft2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'freetype_2.2.1-5ubuntu1.1.dsc'
Skipping already downloaded file 'freetype_2.2.1.orig.tar.gz'
Skipping already downloaded file 'freetype_2.2.1-5ubuntu1.1.diff.gz'
Skipping already downloaded file 'libcairo_1.4.2-0ubuntu1.dsc'
Skipping already downloaded file 'libcairo_1.4.2.orig.tar.gz'
Skipping already downloaded file 'libcairo_1.4.2-0ubuntu1.diff.gz'
Skipping already downloaded file 'xft_2.1.12-1.dsc'
Skipping already downloaded file 'xft_2.1.12.orig.tar.gz'
Skipping already downloaded file 'xft_2.1.12-1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in freetype-2.2.1
Skipping unpack of already unpacked source in libcairo-1.4.2
Skipping unpack of already unpacked source in xft-2.1.12
root@danny-desktop:/tmp/fonts# dir
freetype-2.2.1                     libcairo_1.4.2-0ubuntu1.dsc
freetype_2.2.1-5ubuntu1.1.diff.gz  libcairo_1.4.2.orig.tar.gz
freetype_2.2.1-5ubuntu1.1.dsc      xft-2.1.12
freetype_2.2.1.orig.tar.gz         xft_2.1.12-1.diff.gz
libcairo-1.4.2                     xft_2.1.12-1.dsc
libcairo_1.4.2-0ubuntu1.diff.gz    xft_2.1.12.orig.tar.gz
root@danny-desktop:/tmp/fonts# sudo cowbuilder --build freetype_2.3.5-1mlind1~feisty0.1.dsc
File not found: freetype_2.3.5-1mlind1~feisty0.1.dsc
root@danny-desktop:/tmp/fonts#

---

### Post by giorgosts on 2007-08-04
do a double tab to find the exact name(s) of the .dsc file(s), which might not be the same as the one(s) you're pasting into the terminal

Mine worked like a charm Thanks mlind!

---

### Post by dannymichel on 2007-08-04
> **mlind said:**
> 

Then install libfreetype6_*.deb, libcairo2_*.deb and libxft2_*.deb binaries from ~/pbuilder/results. Only 3 packages should get installed.

Hoe do I do that?

---

### Post by mlind on 2007-08-05
> **dannymichel said:**
> Hoe do I do that?

```

cd ~/pbuilder/results
sudo dpkg -i libfreetype6_*.deb libcairo2_*.deb lib libxft2_*.deb

```

---

### Post by dannymichel on 2007-08-05
> **mlind said:**
> ```

cd ~/pbuilder/results
sudo dpkg -i libfreetype6_*.deb libcairo2_*.deb lib libxft2_*.deb

```
It's weird.
~/pbuilder/results does not exist

---

### Post by dannymichel on 2007-08-05
> **dannymichel said:**
> It's weird.
~/pbuilder/results does not exist

danny@danny-desktop:~$ sudo su
Password:
root@danny-desktop:/home/danny# cd ~/pbuilder/results
bash: cd: /root/pbuilder/results: No such file or directory
root@danny-desktop:/home/danny#

---

### Post by hugmenot on 2007-08-06
> **dannymichel said:**
> danny@danny-desktop:~$ sudo su
Password:
root@danny-desktop:/home/danny# cd ~/pbuilder/results
bash: cd: /root/pbuilder/results: No such file or directory
root@danny-desktop:/home/danny#

Well, root&#8217;s ~ and danny&#8217;s ~ are not the same. Enter /home/danny explicitly for that.

---

### Post by Trinità on 2007-08-06
The Moshen repo are still down?

I've got error 404 :(

---

### Post by dannymichel on 2007-08-06
> **hugmenot said:**
> Well, root&#8217;s ~ and danny&#8217;s ~ are not the same. Enter /home/danny explicitly for that.
```
tartup-tasks_0.3.8-1_i386.deb' to `/var/cache/pbuilder/aptcache/startup-tasks_0.3.8-1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/belocs-locales-bin_2.4-2ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/belocs-locales-bin_2.4-2ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/ncurses-base_5.5-5ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/ncurses-base_5.5-5ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/gcc-4.1-base_4.1.2-0ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/gcc-4.1-base_4.1.2-0ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/grep_2.5.1.ds2-6build1_i386.deb' to `/var/cache/pbuilder/aptcache/grep_2.5.1.ds2-6build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/vim-tiny_1%3a7.0-164+1ubuntu7_i386.deb' to `/var/cache/pbuilder/aptcache/vim-tiny_1%3a7.0-164+1ubuntu7_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/perl-modules_5.8.8-7build1_all.deb' to `/var/cache/pbuilder/aptcache/perl-modules_5.8.8-7build1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libcap1_1%3a1.10-14_i386.deb' to `/var/cache/pbuilder/aptcache/libcap1_1%3a1.10-14_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libcomerr2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libdb4.4_4.4.20-8ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libdb4.4_4.4.20-8ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libgdbm3_1.8.3-3_i386.deb' to `/var/cache/pbuilder/aptcache/libgdbm3_1.8.3-3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/laptop-detect_0.12.1-ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/laptop-detect_0.12.1-ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libc6_2.5-0ubuntu14_i386.deb' to `/var/cache/pbuilder/aptcache/libc6_2.5-0ubuntu14_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/wireless-tools_28-1ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/wireless-tools_28-1ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/linux-sound-base_1.0.13-3ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/linux-sound-base_1.0.13-3ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/upstart-compat-sysv_0.3.8-1_i386.deb' to `/var/cache/pbuilder/aptcache/upstart-compat-sysv_0.3.8-1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/xkb-data_0.9-4ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/xkb-data_0.9-4ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/aptitude_0.4.4-1ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/aptitude_0.4.4-1ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libuuid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libuuid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libdevmapper1.02_2%3a1.02.08-1ubuntu10_i386.deb' to `/var/cache/pbuilder/aptcache/libdevmapper1.02_2%3a1.02.08-1ubuntu10_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/python-minimal_2.5.1~rc1-0ubuntu3_all.deb' to `/var/cache/pbuilder/aptcache/python-minimal_2.5.1~rc1-0ubuntu3_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/dhcp3-common_3.0.4-12ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/dhcp3-common_3.0.4-12ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/apt_0.6.46.4ubuntu10_i386.deb' to `/var/cache/pbuilder/aptcache/apt_0.6.46.4ubuntu10_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/usbutils_0.72-7ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/usbutils_0.72-7ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/gnupg_1.4.6-1ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/gnupg_1.4.6-1ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/update-inetd_4.27-0.2_all.deb' to `/var/cache/pbuilder/aptcache/update-inetd_4.27-0.2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/sysv-rc_2.86.ds1-14.1ubuntu18_all.deb' to `/var/cache/pbuilder/aptcache/sysv-rc_2.86.ds1-14.1ubuntu18_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/mktemp_1.5-2_i386.deb' to `/var/cache/pbuilder/aptcache/mktemp_1.5-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libopencdk8_0.5.9-2build1_i386.deb' to `/var/cache/pbuilder/aptcache/libopencdk8_0.5.9-2build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libblkid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libblkid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/procps_1%3a3.2.7-3ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/procps_1%3a3.2.7-3ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/apt-utils_0.6.46.4ubuntu10_i386.deb' to `/var/cache/pbuilder/aptcache/apt-utils_0.6.46.4ubuntu10_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libslang2_2.0.6-4build1_i386.deb' to `/var/cache/pbuilder/aptcache/libslang2_2.0.6-4build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libbz2-1.0_1.0.3-6build1_i386.deb' to `/var/cache/pbuilder/aptcache/libbz2-1.0_1.0.3-6build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/gettext-base_0.16.1-1ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/gettext-base_0.16.1-1ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/dpkg_1.13.24ubuntu6_i386.deb' to `/var/cache/pbuilder/aptcache/dpkg_1.13.24ubuntu6_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/tzdata_2007b-0ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/tzdata_2007b-0ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/whiptail_0.52.2-8ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/whiptail_0.52.2-8ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libnewt0.52_0.52.2-8ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libnewt0.52_0.52.2-8ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/upstart_0.3.8-1_i386.deb' to `/var/cache/pbuilder/aptcache/upstart_0.3.8-1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/net-tools_1.60-17ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/net-tools_1.60-17ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libklibc_1.4.30-3ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libklibc_1.4.30-3ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libtext-wrapi18n-perl_0.06-5_all.deb' to `/var/cache/pbuilder/aptcache/libtext-wrapi18n-perl_0.06-5_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/gzip_1.3.9-2_i386.deb' to `/var/cache/pbuilder/aptcache/gzip_1.3.9-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/readline-common_5.2-2ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/readline-common_5.2-2ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libacl1_2.2.42-1ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libacl1_2.2.42-1ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/netbase_4.27ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/netbase_4.27ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/alsa-base_1.0.13-3ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/alsa-base_1.0.13-3ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/volumeid_108-0ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/volumeid_108-0ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/netcat_1.10-32_i386.deb' to `/var/cache/pbuilder/aptcache/netcat_1.10-32_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/ncurses-bin_5.5-5ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/ncurses-bin_5.5-5ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/bsdutils_1%3a2.12r-17ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/bsdutils_1%3a2.12r-17ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/dmsetup_2%3a1.02.08-1ubuntu10_i386.deb' to `/var/cache/pbuilder/aptcache/dmsetup_2%3a1.02.08-1ubuntu10_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/e2fsprogs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/e2fsprogs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/bash_3.2-0ubuntu7_i386.deb' to `/var/cache/pbuilder/aptcache/bash_3.2-0ubuntu7_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/mawk_1.3.3-11ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/mawk_1.3.3-11ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/base-passwd_3.5.11_i386.deb' to `/var/cache/pbuilder/aptcache/base-passwd_3.5.11_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/dhcp3-client_3.0.4-12ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/dhcp3-client_3.0.4-12ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpopt0_1.10-3build1_i386.deb' to `/var/cache/pbuilder/aptcache/libpopt0_1.10-3build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/iputils-ping_3%3a20020927-3.1ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/iputils-ping_3%3a20020927-3.1ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libgpg-error0_1.4-2build1_i386.deb' to `/var/cache/pbuilder/aptcache/libgpg-error0_1.4-2build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/module-init-tools_3.3-pre3-1ubuntu7_i386.deb' to `/var/cache/pbuilder/aptcache/module-init-tools_3.3-pre3-1ubuntu7_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libsepol1_1.14-2build1_i386.deb' to `/var/cache/pbuilder/aptcache/libsepol1_1.14-2build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/perl_5.8.8-7build1_i386.deb' to `/var/cache/pbuilder/aptcache/perl_5.8.8-7build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpam-runtime_0.79-4ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/libpam-runtime_0.79-4ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/e2fslibs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/e2fslibs_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/gpgv_1.4.6-1ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/gpgv_1.4.6-1ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpam-modules_0.79-4ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libpam-modules_0.79-4ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/tasksel-data_2.59ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/tasksel-data_2.59ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libsysfs2_2.1.0-1build1_i386.deb' to `/var/cache/pbuilder/aptcache/libsysfs2_2.1.0-1build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpci2_2%3a2.1.11-3build1_i386.deb' to `/var/cache/pbuilder/aptcache/libpci2_2%3a2.1.11-3build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/wpasupplicant_0.5.7-0ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/wpasupplicant_0.5.7-0ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/tar_1.16-2_i386.deb' to `/var/cache/pbuilder/aptcache/tar_1.16-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libncurses5_5.5-5ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libncurses5_5.5-5ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/ubuntu-keyring_2005.01.12.1_all.deb' to `/var/cache/pbuilder/aptcache/ubuntu-keyring_2005.01.12.1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpam-foreground_0.3_i386.deb' to `/var/cache/pbuilder/aptcache/libpam-foreground_0.3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/python2.5_2.5.1~rc1-0ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/python2.5_2.5.1~rc1-0ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/udev_108-0ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/udev_108-0ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/lsb-release_3.1-22ubuntu3_all.deb' to `/var/cache/pbuilder/aptcache/lsb-release_3.1-22ubuntu3_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/tasksel_2.59ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/tasksel_2.59ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/liblzo1_1.08-3_i386.deb' to `/var/cache/pbuilder/aptcache/liblzo1_1.08-3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/system-services_0.3.8-1_i386.deb' to `/var/cache/pbuilder/aptcache/system-services_0.3.8-1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/login_1%3a4.0.18.1-6ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/login_1%3a4.0.18.1-6ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/pcmciautils_014-3ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/pcmciautils_014-3ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/util-linux_2.12r-17ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/util-linux_2.12r-17ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7_i386.deb' to `/var/cache/pbuilder/aptcache/vim-common_1%3a7.0-164+1ubuntu7_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/eject_2.1.4-2.1ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/eject_2.1.4-2.1ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libdb4.3_4.3.29-6build1_i386.deb' to `/var/cache/pbuilder/aptcache/libdb4.3_4.3.29-6build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/python2.5-minimal_2.5.1~rc1-0ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/python2.5-minimal_2.5.1~rc1-0ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/diff_2.8.1-11ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/diff_2.8.1-11ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/console-tools_1%3a0.2.3dbs-65ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/console-tools_1%3a0.2.3dbs-65ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/hostname_2.93build1_i386.deb' to `/var/cache/pbuilder/aptcache/hostname_2.93build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libtext-iconv-perl_1.4-3_i386.deb' to `/var/cache/pbuilder/aptcache/libtext-iconv-perl_1.4-3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/debconf_1.5.13ubuntu1_all.deb' to `/var/cache/pbuilder/aptcache/debconf_1.5.13ubuntu1_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libss2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libss2_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libvolume-id0_108-0ubuntu4_i386.deb' to `/var/cache/pbuilder/aptcache/libvolume-id0_108-0ubuntu4_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libgnutls13_1.4.4-3build1_i386.deb' to `/var/cache/pbuilder/aptcache/libgnutls13_1.4.4-3build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libsasl2-modules_2.1.22.dfsg1-8ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libsasl2-modules_2.1.22.dfsg1-8ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libtext-charwidth-perl_0.04-4build1_i386.deb' to `/var/cache/pbuilder/aptcache/libtext-charwidth-perl_0.04-4build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libfribidi0_0.10.7-4build1_i386.deb' to `/var/cache/pbuilder/aptcache/libfribidi0_0.10.7-4build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/ifupdown_0.6.8ubuntu6_i386.deb' to `/var/cache/pbuilder/aptcache/ifupdown_0.6.8ubuntu6_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libattr1_1%3a2.4.32-1.1ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libattr1_1%3a2.4.32-1.1ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/locales_2.3.23_all.deb' to `/var/cache/pbuilder/aptcache/locales_2.3.23_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/iproute_20061002-3ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/iproute_20061002-3ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libssl0.9.8_0.9.8c-4build1_i386.deb' to `/var/cache/pbuilder/aptcache/libssl0.9.8_0.9.8c-4build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libselinux1_1.32-3ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/libselinux1_1.32-3ubuntu1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/ubuntu-minimal_1.43_i386.deb' to `/var/cache/pbuilder/aptcache/ubuntu-minimal_1.43_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/klibc-utils_1.4.30-3ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/klibc-utils_1.4.30-3ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/alsa-utils_1.0.13-1ubuntu5_i386.deb' to `/var/cache/pbuilder/aptcache/alsa-utils_1.0.13-1ubuntu5_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libdbus-1-3_1.0.2-1ubuntu3_i386.deb' to `/var/cache/pbuilder/aptcache/libdbus-1-3_1.0.2-1ubuntu3_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/perl-base_5.8.8-7build1_i386.deb' to `/var/cache/pbuilder/aptcache/perl-base_5.8.8-7build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/makedev_2.3.1-83ubuntu2_all.deb' to `/var/cache/pbuilder/aptcache/makedev_2.3.1-83ubuntu2_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libusb-0.1-4_2%3a0.1.12-2_i386.deb' to `/var/cache/pbuilder/aptcache/libusb-0.1-4_2%3a0.1.12-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/findutils_4.2.28-2_i386.deb' to `/var/cache/pbuilder/aptcache/findutils_4.2.28-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libc6-i686_2.5-0ubuntu14_i386.deb' to `/var/cache/pbuilder/aptcache/libc6-i686_2.5-0ubuntu14_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/adduser_3.100_all.deb' to `/var/cache/pbuilder/aptcache/adduser_3.100_all.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb' to `/var/cache/pbuilder/aptcache/libsigc++-2.0-0c2a_2.0.17-2build1_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/libpam0g_0.79-4ubuntu2_i386.deb' to `/var/cache/pbuilder/aptcache/libpam0g_0.79-4ubuntu2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/mii-diag_2.11-2_i386.deb' to `/var/cache/pbuilder/aptcache/mii-diag_2.11-2_i386.deb': File exists
ln: creating hard link `/var/cache/pbuilder/build//2402/var/cache/apt/archives/pciutils_1%3a2.2.4-1ubuntu1_i386.deb' to `/var/cache/pbuilder/aptcache/pciutils_1%3a2.2.4-1ubuntu1_i386.deb': File exists
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
apt is already the newest version.
The following extra packages will be installed:
  binutils cpp cpp-4.1 g++ g++-4.1 gcc gcc-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev make patch
Suggested packages:
  binutils-doc cpp-doc gcc-4.1-locales debian-keyring gcc-4.1-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc
  libc6-dev-amd64 lib64gcc1 glibc-doc libstdc++6-4.1-doc make-doc ed diff-doc
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1
  libc6-dev libstdc++6-4.1-dev linux-libc-dev make patch
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.9MB of archives.
After unpacking 49.7MB of additional disk space will be used.
Selecting previously deselected package binutils.
(Reading database ... 10099 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.17.20070103cvs-0ubuntu2_i386.deb) ...
Selecting previously deselected package linux-libc-dev.
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.20-15.27_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.5-0ubuntu14_i386.deb) ...
Selecting previously deselected package cpp-4.1.
Unpacking cpp-4.1 (from .../cpp-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package cpp.
Unpacking cpp (from .../cpp_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package gcc-4.1.
Unpacking gcc-4.1 (from .../gcc-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package libstdc++6-4.1-dev.
Unpacking libstdc++6-4.1-dev (from .../libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++-4.1.
Unpacking g++-4.1 (from .../g++-4.1_4.1.2-0ubuntu4_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.1.2-1ubuntu1_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../make_3.81-3build1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3_i386.deb) ...
Setting up binutils (2.17.20070103cvs-0ubuntu2) ...

Setting up linux-libc-dev (2.6.20-15.27) ...
Setting up libc6-dev (2.5-0ubuntu14) ...
Setting up cpp-4.1 (4.1.2-0ubuntu4) ...
Setting up cpp (4.1.2-1ubuntu1) ...

Setting up gcc-4.1 (4.1.2-0ubuntu4) ...
Setting up gcc (4.1.2-1ubuntu1) ...

Setting up make (3.81-3build1) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
Setting up libstdc++6-4.1-dev (4.1.2-0ubuntu4) ...
Setting up g++-4.1 (4.1.2-0ubuntu4) ...
Setting up g++ (4.1.2-1ubuntu1) ...

Setting up build-essential (11.3) ...
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> creating base tarball [/var/cache/pbuilder/base.tgz]
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//2402 and its subdirectories
danny@danny-desktop:/tmp/fonts$ nano ~/.pbuilderrc
danny@danny-desktop:/tmp/fonts$ mkdir -p ~/pbuilder/result
danny@danny-desktop:/tmp/fonts$ mkdir ~/pbuilder/hook.d
danny@danny-desktop:/tmp/fonts$ nano ~/pbuilder/hook.d/D70results
danny@danny-desktop:/tmp/fonts$ sudo cowbuilder --build xft
xft-2.1.12/             xft_2.1.12-1.dsc        
xft_2.1.12-1.diff.gz    xft_2.1.12.orig.tar.gz  
danny@danny-desktop:/tmp/fonts$ sudo cowbuilder --build xft_2.1.12-1.dsc
 -> Copying COW directory
 -> Invoking pbuilder
/home/danny/.pbuilderrc: line 28: unexpected EOF while looking for matching `"'
 -> Cleaning COW directory
danny@danny-desktop:/tmp/fonts$ cd ..
danny@danny-desktop:/tmp$ cd ..
danny@danny-desktop:/$ sudo aptitude install cowdancer pbuilder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
danny@danny-desktop:/$ sudo cowbuilder --create
 -> Invoking pbuilder
/home/danny/.pbuilderrc: line 28: unexpected EOF while looking for matching `"'
danny@danny-desktop:/$ cd /tmp/fonts
danny@danny-desktop:/tmp/fonts$ apt-get source freetype libcairo2 libxft2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Skipping already downloaded file 'freetype_2.2.1-5ubuntu1.1.dsc'
Skipping already downloaded file 'freetype_2.2.1.orig.tar.gz'
Skipping already downloaded file 'freetype_2.2.1-5ubuntu1.1.diff.gz'
Skipping already downloaded file 'libcairo_1.4.2-0ubuntu1.dsc'
Skipping already downloaded file 'libcairo_1.4.2.orig.tar.gz'
Skipping already downloaded file 'libcairo_1.4.2-0ubuntu1.diff.gz'
Skipping already downloaded file 'xft_2.1.12-1.dsc'
Skipping already downloaded file 'xft_2.1.12.orig.tar.gz'
Skipping already downloaded file 'xft_2.1.12-1.diff.gz'
Need to get 0B of source archives.
Skipping unpack of already unpacked source in freetype-2.2.1
Skipping unpack of already unpacked source in libcairo-1.4.2
Skipping unpack of already unpacked source in xft-2.1.12
danny@danny-desktop:/tmp/fonts$ gedit ~/.pbuilderrc
/home/danny/.themes/MurrinaNeoAquaIsh/gtk-2.0/gtkrc:172: Unable to locate image file in pixmap_path: "handle-v.png"
/home/danny/.themes/MurrinaNeoAquaIsh/gtk-2.0/gtkrc:175: Overlay image options specified without filename
/home/danny/.themes/MurrinaNeoAquaIsh/gtk-2.0/gtkrc:179: Unable to locate image file in pixmap_path: "handle-h.png"
/home/danny/.themes/MurrinaNeoAquaIsh/gtk-2.0/gtkrc:182: Overlay image options specified without filename
/home/danny/.themes/MurrinaNeoAquaIsh/gtk-2.0/gtkrc:204: Unable to locate image file in pixmap_path: "panel.png"
danny@danny-desktop:/tmp/fonts$ cd ..
danny@danny-desktop:/tmp$ cd ..
danny@danny-desktop:/$ cd ~/pbuilder/results
bash: cd: /home/danny/pbuilder/results: No such file or directory
danny@danny-desktop:/$ 

```

---

### Post by mlind on 2007-08-07
@dannymichel
This is bit offtopic, but your ~/.pbuilderrc is messed up. You're probably missing a " -mark somewhere around line 28 as the error says.

---

### Post by zuzuzzzip on 2007-08-07
it does not want to add the RAOFS gpg key

---

### Post by zuzuzzzip on 2007-08-07
> **dannymichel said:**
> danny@danny-desktop:~$ sudo su
Password:
root@danny-desktop:/home/danny# cd ~/pbuilder/results
bash: cd: /root/pbuilder/results: No such file or directory
root@danny-desktop:/home/danny#
isn't it ~/.pbuilder/results?

you forgot the dot imo

---

### Post by mlind on 2007-08-07
> **zuzuzzzip said:**
> isn't it ~/.pbuilder/results?

you forgot the dot imo

no, without the dot..

---

### Post by ablewisuk on 2007-08-11
If you get an error running the line:

```
sudo cowbuilder --build libcairo_1.4.10-1turner3~feisty0.1.dsc
```

Try removing the suggested

```
PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi
```

from ~/.pbuilderrc.

---

### Post by mlind on 2007-08-11
> **ablewisuk said:**
> If you get an error running the line:

```
sudo cowbuilder --build libcairo_1.4.10-1turner3~feisty0.1.dsc
```

Try removing the suggested

```
PBUILDERSATISFYDEPENDSCMD=/usr/lib/pbuilder/pbuilder-satisfydepends-gdebi
```

from ~/.pbuilderrc.

yes, there's a bug in **pbuilder-satisfydepends-gdebi** script that doesn't allow to install unauthenticated packages.

In /usr/lib/pbuilder/pbuilder-satisfydepends-gdebi, replace
```

$CHROOTEXEC /usr/bin/apt-get install -y $INSTALL

```
with
```

$CHROOTEXEC /usr/bin/apt-get install -y **--force-yes** $INSTALL

```

---

### Post by rdd on 2007-08-15
Worked like a charm for me. I used the second method to add the gpg key. 

Nice one. Thank you

---

### Post by jayson.rowe on 2007-08-15
any news on the AMD64 repo?
this is seriously gonna cuase me to switch distros - i've never had crappy fonts like this until ubuntu....

---

### Post by jayson.rowe on 2007-08-15
> **jayson.rowe said:**
> any news on the AMD64 repo?
this is seriously gonna cuase me to switch distros - i've never had crappy fonts like this until ubuntu....

nevermind - reinstalled w/ 32-bit - should be a bit less hassle all around...from what I've read I'm not really losing anything...and so far, it feels FASTER than the AMD64 did...odd.

---

### Post by subru77 on 2007-08-19
Is this thread dead ? 

I am still looking for a solution for AMD64 ? Any advice ?

---

### Post by mlind on 2007-08-20
> **subru77 said:**
> Is this thread dead ? 

I am still looking for a solution for AMD64 ? Any advice ?

hi subru77, If you're feeling adventurous or desperate enough, you can try to self-compile the required packages. Quick and (less) dirty way is to follow [http://ubuntuforums.org/showpost.php?p=3121797&postcount=281](http://ubuntuforums.org/showpost.php?p=3121797&postcount=281). If you bump into a error where your custom packages cannot be authenticated by apt when calculating build-deps see [http://ubuntuforums.org/showpost.php?p=3171418&postcount=298](http://ubuntuforums.org/showpost.php?p=3171418&postcount=298).

I hope this helps.

---

### Post by RAOF on 2007-08-20
I'm waiting for Seveas to release falcon 2 beta 3, which will make the life of an AMD64 repository administrator much easier.  It should be out soon, and then so will the AMD64 packages.

---

### Post by rainwalker on 2007-08-22
Will this really cause a visible change in fonts?

---

### Post by subru77 on 2007-08-23
Thanks much for the direction. I will try to follow it : )

I love this forum. So much helpful

---

### Post by mlind on 2007-08-23
> **rainwalker said:**
> Will this really cause a visible change in fonts?

There are visible changes in font rendering, at least with LCD panels. Results have been somewhat mixed, but I suggest you to try it out yourself.

---

### Post by rainwalker on 2007-08-23
> **mlind said:**
> There are visible changes in font rendering, at least with LCD panels. Results have been somewhat mixed, but I suggest you to try it out yourself.

Hm...alright then.
So I just add those two lines to my sources.list and then update?

---

### Post by sudhu on 2007-08-23
> **rainwalker said:**
> Hm...alright then.
So I just add those two lines to my sources.list and then update?

It definitely changed the fonts rendering for me. It looks good now.
Yes, just add the repos to the sources.list then do apt-get update and upgrade

---

### Post by rainwalker on 2007-08-23
Everything looks the same to me...

---

### Post by jayson.rowe on 2007-08-23
> **jayson.rowe said:**
> nevermind - reinstalled w/ 32-bit - should be a bit less hassle all around...from what I've read I'm not really losing anything...and so far, it feels FASTER than the AMD64 did...odd.

Well, I didn't stay w/ 32 bit long - it didn't take long for me to start noticing a difference in performance. I did however finally compile AMD64 packages myself, and I'm assuming that anyone can use the packages I made...anyway I uploaded them in a TAR-ball for you if you are interested in trying them out...

[http://www.lamerc.com/uploads/font_packages.tar.gz](http://www.lamerc.com/uploads/font_packages.tar.gz)

Hope this helps someone out.

---

### Post by mlind on 2007-08-23
> **rainwalker said:**
> Everything looks the same to me...

Did you reconfigure fontconfig library and and restart xserver as noted in first post?

---

### Post by rainwalker on 2007-08-23
Um...I'm not sure, actually. I'll go check
(Sorry, I"m not too good with this reconfiguring stuff)

---

### Post by mlind on 2007-08-23
> **rainwalker said:**
> Um...I'm not sure, actually. I'll go check
(Sorry, I"m not too good with this reconfiguring stuff)

That's okay. You should also select 'Subpixel Smoothing' and 'Full Hinting' from the font settings for the best result (in my opinion).

---

### Post by OffHand on 2007-08-24
I am running into dependency problems:

user@ubuntu:~$ sudo aptitude install libfreetype6 libcairo2 libxft2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libcairo2-dev libfreetype6-dev libxft-dev 
The following packages have been automatically kept back:
  kdebase-bin kdebase-kio-plugins kdesktop libkonq4 
The following packages will be upgraded:
  libcairo2 libfreetype6 libxft2 
3 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 921kB of archives. After unpacking 115kB will be used.
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.4.2-0ubuntu1) but 1.4.10-1turner3~feisty0.1 is to be installed.
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5ubuntu1.1) but 2.3.5-1mlind1~feisty0.1 is to be installed.
  libxft-dev: Depends: libxft2 (= 2.1.12-1) but 2.1.12-2turner2~feisty0.1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
libcairo2-dev [1.4.2-0ubuntu1 (feisty, now) -> 1.4.10-1turner3~feisty0.1
(feisty)]
libfreetype6-dev [2.2.1-5ubuntu1.1 (feisty-security, now) ->
2.3.5-1mlind1~feisty0.1 (feisty)]
libxft-dev [2.1.12-1 (feisty, now) -> 2.1.12-2turner2~feisty0.1 (feisty)]

Score is -100

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.

---

### Post by hugmenot on 2007-08-24
Accept. Libs and their -dev packages always come in pairs and have to match.

---

### Post by rainwalker on 2007-08-24
EDIT: I'm kind of getting used to the fonts now, I guess they look a little better (just different). The letters seem more squashed together...? 
I guess it will take a little while to get used to them, but still, my question is the same:

How do I downgrade the packages so it will be like it was before, if I change my mind?

---

### Post by zedpp on 2007-08-24
Thanks for the instructions, Fonts look more than twice as clear.

---

### Post by shanepardue on 2007-08-24
Yeah, I have found this to be absolutely necessary for LCD's and ubuntu. Thanks for the assistance!

---

### Post by mlind on 2007-08-25
> **rainwalker said:**
> EDIT: I'm kind of getting used to the fonts now, I guess they look a little better (just different). The letters seem more squashed together...? 
I guess it will take a little while to get used to them, but still, my question is the same:

How do I downgrade the packages so it will be like it was before, if I change my mind?

You can use synaptic to install libfreetype6, libcairo2 and libxft2 from Ubuntu repositories. If you prefer command-line instead:
```

sudo aptitude install libfreetype6=2.2.1-5ubuntu1.1 libcairo2=1.4.2-0ubuntu1 libxft2=2.1.12-1

```

---

### Post by wersdaluv on 2007-08-26
Why is that, only apps ran as root have subpixel font rendering on my desktop?

See the screenshot. The firefox on the left is ran as root.

---

### Post by mlind on 2007-08-27
> **wersdaluv said:**
> Why is that, only apps ran as root have subpixel font rendering on my desktop?

See the screenshot. The firefox on the left is ran as root.

Do you have ~/.fonts.conf file ? If you do, remove it.

---

### Post by wersdaluv on 2007-08-27
> **mlind said:**
> Do you have ~/.fonts.conf file ? If you do, remove it.

It works now!

This is fantastic! Thanks!

:KS

---

### Post by subru77 on 2007-08-28
> **jayson.rowe said:**
> Well, I didn't stay w/ 32 bit long - it didn't take long for me to start noticing a difference in performance. I did however finally compile AMD64 packages myself, and I'm assuming that anyone can use the packages I made...anyway I uploaded them in a TAR-ball for you if you are interested in trying them out...

[http://www.lamerc.com/uploads/font_packages.tar.gz](http://www.lamerc.com/uploads/font_packages.tar.gz)

Hope this helps someone out.


I will try to use this and update you. 

Thanks in advance :)

---

### Post by kadath on 2007-08-29
These patched libs make my fonts look very nice. However, I've noticed something strange in percent signs as you can see below:

[IMG]http://i12.tinypic.com/6gv7i0z.png[/IMG]

The font is Arial at 16pt (aka 100% for most browsers by default).

This behavior is also seen in AbiWord, although it's not as pronounced.

Not a major hassle, but very strange.

---

### Post by hugmenot on 2007-08-29
Must be a flaw in the autohinter. Bytecode and unhinted don't show this. If you feel strong about it write a report to the freetype devel mailing list. They need to correct stuff like this occasionally.

---

### Post by wersdaluv on 2007-08-30
This is really so nice! I wanna lick my screen every time I see the fonts!

:guitar:

---

### Post by LuisC-SM on 2007-08-31
Hi.
I have a question.
Some time ago, I saw a post where someone; via the command line, had got the Monitor or Screen DPI, so does anyone know how to get it?.

TIA

Luis.

PS. By the way, I've tried to find this old post with no eval.
PS2. I forgot to mention that this instructions worked just wonderfull. THANKS!!!

---

### Post by nick_h on 2007-09-01
To get the DPI, type:
```
xdpyinfo | grep resolution
```
To get screen size, type:
```
xdpyinfo | grep dimensions
```

---

### Post by LuisC-SM on 2007-09-01
> **nick_h said:**
> To get the DPI, type:
```
xdpyinfo | grep resolution
```
To get screen size, type:
```
xdpyinfo | grep dimensions
```

Thanks a lot Nick :D

The command is telling me I have a 115 DPI resolution, should I change it in the "Font Settings" section?  (the default value I have is 96 DPI).

I'm asking these 'cause my fonts are extremely small (I can see them very well but some times it kind of gets my eyes tired).

TIA 

Luis

PS. I have said before that this method really enhanced my fonts. They are now better than XP or vista by far.

---

### Post by LT1Caprice57L on 2007-09-01
EDIT: Solved.

Huge difference, and thnings actually look acceptable under Slight hinting now.  Too bad I didn't get a before screenshot.

---

### Post by beeldings on 2007-09-03
Does anyone have the amd64 versions of these packages or at least the link to a working repo? The amd64 files appear to be missing from the repo:
```

kathodos@scholomance:/etc/apt/sources.list.d$ sudo apt-get install libfreetype6 libcairo2 libxft2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcairo2-dev libfreetype6-dev libxft-dev
Suggested packages:
  libcairo2-doc
The following packages will be upgraded:
  libcairo2 libcairo2-dev libfreetype6 libfreetype6-dev libxft-dev libxft2
6 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 2141kB of archives.
After unpacking 267kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfreetype6-dev libfreetype6 libxft-dev libxft2 libcairo2-dev libcairo2
Install these packages without verification [y/N]? y
Err http://ubuntu.moshen.de feisty/experimental libfreetype6-dev 2.3.3-0mlind1
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libfreetype6 2.3.3-0mlind1
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libxft-dev 2.1.12-1+turner3
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libxft2 2.1.12-1+turner3
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libcairo2-dev 1.4.2-0ubuntu1+turner2
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libcairo2 1.4.2-0ubuntu1+turner2
  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6-dev_2.3.3-0mlind1_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6_2.3.3-0mlind1_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libxft-dev_2.1.12-1+turner3_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libxft2_2.1.12-1+turner3_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2-dev_1.4.2-0ubuntu1+turner2_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2_1.4.2-0ubuntu1+turner2_amd64.deb  404 Not Found

```

---

### Post by LuisC-SM on 2007-09-03
> **beeldings said:**
> Does anyone have the amd64 versions of these packages or at least the link to a working repo? The amd64 files appear to be missing from the repo:
```

kathodos@scholomance:/etc/apt/sources.list.d$ sudo apt-get install libfreetype6 libcairo2 libxft2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcairo2-dev libfreetype6-dev libxft-dev
Suggested packages:
  libcairo2-doc
The following packages will be upgraded:
  libcairo2 libcairo2-dev libfreetype6 libfreetype6-dev libxft-dev libxft2
6 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 2141kB of archives.
After unpacking 267kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libfreetype6-dev libfreetype6 libxft-dev libxft2 libcairo2-dev libcairo2
Install these packages without verification [y/N]? y
Err http://ubuntu.moshen.de feisty/experimental libfreetype6-dev 2.3.3-0mlind1
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libfreetype6 2.3.3-0mlind1
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libxft-dev 2.1.12-1+turner3
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libxft2 2.1.12-1+turner3
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libcairo2-dev 1.4.2-0ubuntu1+turner2
  404 Not Found
Err http://ubuntu.moshen.de feisty/experimental libcairo2 1.4.2-0ubuntu1+turner2
  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6-dev_2.3.3-0mlind1_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libfreetype6_2.3.3-0mlind1_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libxft-dev_2.1.12-1+turner3_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libxft2_2.1.12-1+turner3_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2-dev_1.4.2-0ubuntu1+turner2_amd64.deb  404 Not Found
Failed to fetch http://ubuntu.moshen.de/pool/feisty/experimental/libcairo2_1.4.2-0ubuntu1+turner2_amd64.deb  404 Not Found

```
What about:
```
wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
```

or for experimental:
```
gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -
```

Hope this helps
Luis

---

### Post by thcuser on 2007-09-03
I wanted to update my amd64 system too and got the same errors: "Failed to fetch..." and "404 Not Found...". Please upload these files to some other location, if you have them.

Thanks in advance.

---

### Post by beeldings on 2007-09-03
> **LuisC-SM said:**
> What about:
```
wget http://ubuntu.moshen.de/2F306651.gpg -O- | sudo apt-key add -
```

or for experimental:
```
gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -
```

Hope this helps
Luis

I tried that and I either get a 404 file not found error or a malformed release file error, depending upon the repo I used. I tried the repo from Raof and the experimental repo.

---

### Post by Dark Neutron on 2007-09-03
> **thcuser said:**
> I wanted to update my amd64 system too and got the same errors: "Failed to fetch..." and "404 Not Found...". Please upload these files to some other location, if you have them.

Thanks in advance.

Same here.  The AMD64 sites seem to be down.

---

### Post by mlind on 2007-09-03
hiya,

people after amd64 packages probably need to self-compile the packages currently. There's related information in page 31 of this thread.

---

### Post by mr4thjuly on 2007-09-06
Can those Feisty packages be ported to Dapper?
Thanks.

---

### Post by hugmenot on 2007-09-15
Hey mlind, this looks like something that could solve the shortage of AMD64 builds.

[https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)

---

### Post by wersdaluv on 2007-09-15
How do I apply this font to OpenOffice.org apps? All my other apps already have the improved subpixel font rendering.

---

### Post by dogson on 2007-09-18
> **mlind said:**
> hi subru77, If you're feeling adventurous or desperate enough, you can try to self-compile the required packages. Quick and (less) dirty way is to follow [http://ubuntuforums.org/showpost.php?p=3121797&postcount=281](http://ubuntuforums.org/showpost.php?p=3121797&postcount=281). If you bump into a error where your custom packages cannot be authenticated by apt when calculating build-deps see [http://ubuntuforums.org/showpost.php?p=3171418&postcount=298](http://ubuntuforums.org/showpost.php?p=3171418&postcount=298).

I hope this helps.

Thank you for this, worked great.

---

### Post by mlind on 2007-09-18
> **hugmenot said:**
> Hey mlind, this looks like something that could solve the shortage of AMD64 builds.

[https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)

hum.. this sounds doable. I actually tried to upload patched freetype in PPA, but the package was missing debian/copyright file and upload was rejected. Would you/someone like to provide a copyright file for the package? :mrgreen: as I'm too lazy ?

---

### Post by mlind on 2007-09-18
> **wersdaluv said:**
> How do I apply this font to OpenOffice.org apps? All my other apps already have the improved subpixel font rendering.

I guess the oo is somewhat 'broken' with newer freetype regarding to font rendering. This issue has been discussed in this thread (somewhere). I'm not sure if anyone found a workaround for the problem. Have you tried LD_PRELOADing earlier libfreetype6.so when launching the oo yet ?

---

### Post by mindtrick on 2007-09-20
I have a question. When Gutsy comes out next month, how should we do the upgrading? Should we restore the original files and do the distro upgrade or just upgrade? Is it likely to cause problems with the upgrade process?

---

### Post by hugmenot on 2007-09-20
Luckily in alphanumeric sorting ubuntu comes after mlind and turner, so theres nothing you need to do, you will receive the updates from official gutsy automatically.

---

### Post by mindtrick on 2007-09-20
Thanks! Good news.

---

### Post by hugmenot on 2007-09-21
These patches will ship with official Gutsy unless there is a clear opposition from beta-testers during the next weeks.

The developers solicit feedback on which settings will make the best default.

[Go and vote]("http://ubuntuforums.org/showthread.php?t=555964") (hint: for slight)

---

### Post by mlind on 2007-09-21
> **mindtrick said:**
> I have a question. When Gutsy comes out next month, how should we do the upgrading? Should we restore the original files and do the distro upgrade or just upgrade? Is it likely to cause problems with the upgrade process?

what hugmenot said, except that vote for "full and enable monospace too"  :mrgreen:
(the naming thingy was chosen so that new ubuntu packages would always be considered newer, less hassle for upgraders)

---

### Post by mindtrick on 2007-09-22
Thanks for reminding that. I use full hinting. It has by far the most votes at the moment.

---

### Post by PC-Ente on 2007-09-22
Hi

Would be nice if someone can upload the 64bit-packages again. So i can install them... 

Thx

---

### Post by RAOF on 2007-09-23
> **PC-Ente said:**
> Hi

Would be nice if someone can upload the 64bit-packages again. So i can install them... 

Thx

The PPA should be building both i386 & AMD64 packages.

---

### Post by oayfer on 2007-09-27
I installed the patched packages and decided they did not improve font rendering on my screen.

Now when I try to "force version" in synaptic to go back to the ubuntu packages, the dependencies require uninstalling X along with hundreds of other packages.

Is there a clean way to go back to the old versions without going through this mess?

Thanks.

---

### Post by ngc2997 on 2007-09-27
Hi,

recently, I've seen a very strange effect of which I am not quite sure where it comes from, but might be caused by the improved font rendering libraries..

When viewing black (#000000) text on a grey (#dddddd) background, there are visible artifacts within and around letters, appearing as 'flickering' red dots (pixels or sub-pixels) on my TFT screen. I've noticed this first on [www.german-bash.org](www.german-bash.org) (look at the text inside the light grey boxes in the centre of the page), but also e.g. when setting Gnome's panel background colour to #dddddd with black text. (System font Bitstream Vera Sans, 8px)

Could this perhaps be caused by subpixel rendering or another inconsistency in the improved libraries? Actually, when turning subpixel rendering off in the fonts applet, the flicker is gone..

Are there other possible solutions to this?

(Ubuntu 7.04, libcairo2 1.4.10-1turner3, libfreetype6 2.3.5-1mlind1, libxft2 2.1.12-2turner2, all feisty; Gnome 2.18.0, Gtk+ 2.10.11; ATI Radeon 9800 Pro with fglrx driver, TFT over DVI)

Best wishes,
Karsten

---

### Post by hugmenot on 2007-09-27
With flickering, do you mean periodic temporal on-and-off behaviour? Your graphics/display hardware must be be broken.

---

### Post by ngc2997 on 2007-09-27
> **hugmenot said:**
> With flickering, do you mean periodic temporal on-and-off behaviour? Your graphics/display hardware must be be broken.

Yes, that was exactly what I meant. Anyway, seems I've fallen for my faulty DVI cable *sigh*. The effect is gone now, so.. no dice..  :)

Thanks for your patience,
best wishes
Karsten

---

### Post by mlind on 2007-09-27
> **oayfer said:**
> I installed the patched packages and decided they did not improve font rendering on my screen.

Now when I try to "force version" in synaptic to go back to the ubuntu packages, the dependencies require uninstalling X along with hundreds of other packages.

Is there a clean way to go back to the old versions without going through this mess?

Thanks.

hiya, this should work [http://ubuntuforums.org/showpost.php?p=3250376&postcount=319](http://ubuntuforums.org/showpost.php?p=3250376&postcount=319)
make sure you remove the repository from your /etc/apt/sources.list

---

### Post by thcuser on 2007-10-22
I upgraded to the 7.10 release. It seems that rendering is improved here. At least I can see it on some characters which had problems before.

Can anyone confirm that David Turner's subpixel rendering patches are included in the 7.10 release?
And what about patented techniques, are they switch on? If not, what is the best way to switch them on. I am using amd64 build.

Thank you.

---

### Post by mlind on 2007-10-22
> **thcuser said:**
> I upgraded to the 7.10 release. It seems that rendering is improved here. At least I can see it on some characters which had problems before.

Can anyone confirm that David Turner's subpixel rendering patches are included in the 7.10 release?
And what about patented techniques, are they switch on? If not, what is the best way to switch them on. I am using amd64 build.

Thank you.

Turner's subpixel rendering patches for libcairo2 and libxft2 are included and freetype is compiled FT_CONFIG_OPTION_SUBPIXEL_RENDERING enabled in Gutsy. You may want to remove /etc/fonts/conf.d/53-monospace-lcd-filter.conf to get subpixel rendering for small monospace fonts too.

[http://ubuntuforums.org/showthread.php?t=555964](http://ubuntuforums.org/showthread.php?t=555964)

---

### Post by jamesford on 2007-10-23
anyone know how to revert to feisty style rendering? i hate this and it hurts my eyes

---

### Post by 00arthuryu on 2008-01-09
i have a weird effect on mine
all the letters have red beside them and it looks really terrible
and it also hurts my eyes :(
I have included a screenshot

[[IMG]http://img90.imageshack.us/img90/7480/screenshotgooglemozilladh7.th.png[/IMG]](http://img90.imageshack.us/my.php?image=screenshotgooglemozilladh7.png)

---

### Post by Newarz on 2008-05-01
Sometime back I had installed KDE 3.5 in Ubuntu and is still working fine. However, I discovered there's a newer version available now. How do I upgrade it? Thanks for helping.

Newarz

---

