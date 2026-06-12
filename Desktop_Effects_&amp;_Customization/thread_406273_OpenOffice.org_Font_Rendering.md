---
title: "OpenOffice.org Font Rendering"
date: 2007-04-10
forum: Desktop Effects &amp; Customization
---

### Post by skip27 on 2007-04-10
I know this horse has probably been beaten dead a thousand times, but this particular problem is pissing me off a great deal.

Everything about Linux is great... except for the fact that OpenOffice.org has horrendous font rendering.

I've tried using the font replacement table (i.e. Arial instead of Andale Sans UI). Still ugly.
I've tried using LD_PRELOAD=/usr/local/lib/libfreetype.so.6.3.8. Fonts are sharper, but "spidery" and not attractive.

I've tried applying the Turner freetype patches, I've tried dpkg-reconfigure fontconfig-config, I tried adjusting the Font settings in the Preferences menu, I've tried messing around with my .fonts file in my home directory, I've tried installing new fonts altogether, yet nothing seems to be able to recreate the crispness that I find while using MS Office on a Windows platform. Hell, I even tried StarOffice thinking that they improved OO.org, but alas, the same font rendering problems. For as much as I love Linux, and for as technical a user I am, this is almost pushing me to switch back. It is *really* frustrating me.

What do I need to do? There has to be a solution and I refuse to believe otherwise. What am I doing wrong?

---

### Post by NikoC on 2007-04-11
I've been struggling with this one myself without finding a solution that works for me so far, one might consider installing gnome-office instead ;)

---

### Post by phelge on 2007-04-11
The only way I found is to do as follows :

- Do not modify your current desktop font settings (hinting, ...)
- Download freetype-2.1.10 and compile it
- copy the resulting libfreetype.so.6.3.8 in (for example) /opt/openoffice.org2.1/program/filter
- add in the beginning of soffice :
export LD_PRELOAD=/opt/openoffice.org2.1/program/filter/libfreetype.so.6.3.8
- start swriter and you should see nice fonts

Hope this helps

---

### Post by skip27 on 2007-04-11
Thanks phelge, but I've already tried that and I'm still not happy with the fonts. Although, there is one slight difference... I downloaded a precompiled libfreetype.so.6.3.8... did you compile yours by modifying the ftoption.h header file and enabling the bytecode interpreter? Does it make a difference?

Still determined, I am currently recompiling the entire OpenOffice.org suite with the ./configure flags --with-system-freetype, --enable-cairo, and --disable-fontooo. Because I am using the turner libraries ([http://ubuntuforums.org/showthread.php?t=235526](http://ubuntuforums.org/showthread.php?t=235526)) my expectations are high... I just hope these lofty hopes aren't dashed by the time this build finishes. Because OpenOffice.org comes packaged by default without the bytecode interpreter, or any of the other fancy stuff, I'm hoping this will do it.

I'll keep you all posted. I'm not going to switch back to the evil empire just because of this stupid problem.

---

### Post by phelge on 2007-04-12
Hello skip27

I did exactly (no modifs to ftoption.h, ...) what I mentionned in my previous post. I agree there is a difference but as I explained this is the best result I got. See attached screenshot.

Of course, I would be very interested to test your self compiled Openoffice packages :)

Thanks and regards

---

### Post by skip27 on 2007-04-13
Amazing... the recompile didn't make one iota of a difference. Isn't this a curious thing...

EDIT: I've been tinkering around with my .fonts.conf file, and a number of other things. I have a busy weekend, but I'll eventually post settings, screenshots, etc. I think I've gotten things to a point where they are very acceptable.

---

### Post by mrk112 on 2007-04-13
phelge, could you tell me what font settings you're using for Gnome? I've been messing around with my fonts for ages and I still haven't got them looking as good as the ones in your screenshot..

---

### Post by phelge on 2007-04-13
Hello mrk112, Look at the thread : Improved subpixel font rendering packages for Edgy. In the last pages I posted some comments and screenshots.

---

### Post by skip27 on 2007-04-13
Wow, I'm excited! This is preliminary, and maybe its just my imagination kicking in, but I think I finally fixed it once and for all. I'll post later tonight all my findings, procedures, etc... I've got a busy day.

I added autohint to my .fonts.conf and it made a significant difference. Is the pre-built version of OpenOffice compiled to work with the system fontconfig library? If it isn't, that would explain the problems that virtually everyone is having. When I recompiled OpenOffice, I made sure to compile it with --disable-fontooo, which makes it work with the system fontconfig library.

EDIT: sorry it's taken me so long to post the HOWTO. I promise I'll do it late next week once I've finished my exams in school.

---

### Post by igknighted on 2007-04-13
try running the gconf-editor and enabling full anti-aliasing for fonts and turning on sub-pixel hinting if you are using an LCD (it works ok for CRTs as well I guess).  This made my fonts look better than windows fonts.

---

### Post by koshatnik on 2007-04-14
> **skip27 said:**
> Thanks phelge, but I've already tried that and I'm still not happy with the fonts. Although, there is one slight difference... I downloaded a precompiled libfreetype.so.6.3.8... did you compile yours by modifying the ftoption.h header file and enabling the bytecode interpreter? Does it make a difference?

Still determined, I am currently recompiling the entire OpenOffice.org suite with the ./configure flags --with-system-freetype, --enable-cairo, and --disable-fontooo. Because I am using the turner libraries ([http://ubuntuforums.org/showthread.php?t=235526](http://ubuntuforums.org/showthread.php?t=235526)) my expectations are high... I just hope these lofty hopes aren't dashed by the time this build finishes. Because OpenOffice.org comes packaged by default without the bytecode interpreter, or any of the other fancy stuff, I'm hoping this will do it.

I'll keep you all posted. I'm not going to switch back to the evil empire just because of this stupid problem.

Can someone post a quick how-to for this please? :D

---

### Post by stchman on 2007-04-17
I also struggled with this and I found the solution.  I have it here on my website:

[http://www.stchman.com/tweaks.html](http://www.stchman.com/tweaks.html)

It is under the Openoffice.org tweaks.

The anti-aliasing for fonts is a default 8 pixels.  Set it to 25 and they will look way better.  I have only tried this with OO 2.2.

I hope this helps.

---

### Post by mr_firefox on 2007-04-22
Due to the font problems, I've ditched OpenOffice Writer and started to use AbiWord instead. The fonts look great now! Give it a whirl.     :)

---

### Post by Randall311 on 2007-05-01
> **skip27 said:**
> Wow, I'm excited! This is preliminary, and maybe its just my imagination kicking in, but I think I finally fixed it once and for all. I'll post later tonight all my findings, procedures, etc... I've got a busy day.

I added autohint to my .fonts.conf and it made a significant difference. Is the pre-built version of OpenOffice compiled to work with the system fontconfig library? If it isn't, that would explain the problems that virtually everyone is having. When I recompiled OpenOffice, I made sure to compile it with --disable-fontooo, which makes it work with the system fontconfig library.

EDIT: sorry it's taken me so long to post the HOWTO. I promise I'll do it late next week once I've finished my exams in school.

Hey skip27 is there any update on your OOo font tweaking progress?  If you could follow up with a screenshot and the steps you took to improve OOo font rendering I would really appreciate it!  I'm running Ubuntu 7.04 with the David Turner sub pixel rendering packages found here [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670).  My desktop looks gorgeous (better then windows and OS X IMHO) except for OpenOffice which looks like somebody threw up all over it.

---

### Post by skip27 on 2007-05-18
I'm struggling to find the time to write a detailed HOWTO (I'm really *that* busy), so here are a few good places to start looking:

[http://www.linuxfromscratch.org/blfs/view/svn/xsoft/openoffice.html](http://www.linuxfromscratch.org/blfs/view/svn/xsoft/openoffice.html)
[http://tools.openoffice.org/dev_docs/build_linux.html](http://tools.openoffice.org/dev_docs/build_linux.html)
[http://wiki.services.openoffice.org/wiki/Building_OpenOffice.org](http://wiki.services.openoffice.org/wiki/Building_OpenOffice.org)

I hate to bring bad news this late, but unfortunately, it seems that I have not fixed the problem with Edgy. Feisty 7.04 seems to have fixed the problem in much the same way that Edgy 6.10 with the LD_PRELOAD fix has, but the font rendering is still nonetheless inferior to how the fonts render in every other application. For instance, in Abiword, everything looks gorgeous. It seems that I may have to switch word processors for now.

Also, it is worth noting that when I did recompile openoffice, I used --disable-fontooo. However, I did not explicitly use --enable-fontconfig, because when I did a ./configure --help, the only thing it listed relating to 'fontconfig' was --disable-fontconfig, which seems to imply that it comes enabled by default. Then again, I could be wrong. So, alas, it seems that I will have to try another recompile, this time by explicitly using --enable-fontconfig. My theory is that if I use the system fontconfig libraries--the Turner ones--with the fontconfig option, the fonts should render how they are supposed to. If this fails, we can conclude that this problem is simply not fixable at this time. Should this be the case, my recommendation would be to simply use Abiword until the oo.org team gets their priorities straightened out and fixes this.

---

### Post by stchman on 2007-05-18
> **skip27 said:**
> I'm struggling to find the time to write a detailed HOWTO (I'm really *that* busy), so here are a few good places to start looking:

[http://www.linuxfromscratch.org/blfs/view/svn/xsoft/openoffice.html](http://www.linuxfromscratch.org/blfs/view/svn/xsoft/openoffice.html)
[http://tools.openoffice.org/dev_docs/build_linux.html](http://tools.openoffice.org/dev_docs/build_linux.html)
[http://wiki.services.openoffice.org/wiki/Building_OpenOffice.org](http://wiki.services.openoffice.org/wiki/Building_OpenOffice.org)

I hate to bring bad news this late, but unfortunately, it seems that I have not fixed the problem with Edgy. Feisty 7.04 seems to have fixed the problem in much the same way that Edgy 6.10 with the LD_PRELOAD fix has, but the font rendering is still nonetheless inferior to how the fonts render in every other application. For instance, in Abiword, everything looks gorgeous. It seems that I may have to switch word processors for now.

Also, it is worth noting that when I did recompile openoffice, I used --disable-fontooo. However, I did not explicitly use --enable-fontconfig, because when I did a ./configure --help, the only thing it listed relating to 'fontconfig' was --disable-fontconfig, which seems to imply that it comes enabled by default. Then again, I could be wrong. So, alas, it seems that I will have to try another recompile, this time by explicitly using --enable-fontconfig. My theory is that if I use the system fontconfig libraries--the Turner ones--with the fontconfig option, the fonts should render how they are supposed to. If this fails, we can conclude that this problem is simply not fixable at this time. Should this be the case, my recommendation would be to simply use Abiword until the oo.org team gets their priorities straightened out and fixes this.

I just upgraded my laptop to Feisty and Openoffice.org 2.2 is installed.  The fonts are good now.  I have another machine with Edgy and OO2.2 I downloaded from OO's website and the fonts look like cr@p.  I wonder how Ubuntu fixed the problem.

---

### Post by skip27 on 2007-05-20
I'll post a detailed thread on how to recompile openoffice another time. It's almost 1AM and I have plans, believe it or not. But, I will say this: I think we *might* have a winner.

I've attached two screenshots. The most important compile-time options that I used were --disable-fontooo, --enable-fontconfig and --with-system-freetype (assuming the Turner libraries are installed). You see how *remarkably* close it comes to Abiword, and the differences become even smaller when using other fonts, such as Arial or Times New Roman (see screenshot2.jpg). The fonts do seem a bit fuzzy and faint at times, but I wonder if it's something I can adjust to...

I think we've reached our maximum potential. If my theory is correct, it doesn't seem that we can go any further simply because openoffice.org does not know how to interpret freetype's entire set of font rendering techniques, such as autohinting. I can only *guess* that openoffice.org is equipped with a basic level of interpreting freetype capabilities, meaning that things like a fonts.conf file will have little to no effect. I, personally, was unable to change font rendering in oo.org by adjusting my fonts.conf file. Thus, it seems that a particular font rendering scheme has been defaulted into the code. This is why changing your font rendering from best shapes to best contrast, etc. has no effect.

Anyway, my openoffice.org comprehensive recompiling HOWTO will be posted in a day or two. For the impatient who are already savvy enough with recompiling software, here were the compile-time options I used:

./configure --prefix=/opt/openoffice-2.2.0 --enable-lockdown --disable-fontooo --enable-fontconfig --enable-cups --disable-symbols --disable-debug --disable-dbgutil --enable-gtk --enable-gnome-vfs --enable-evolution2 --enable-build-mozilla --without-fonts --with-system-stdlibs --with-system-freetype --with-jdk-home=/usr/lib/jvm/j2sdk1.4.2 --with-use-shell=bash --with-dict --with-myspell-dicts

NOTE: --with-jdk-home may not apply to your specific system! It is advisable that you use Java 1.4.2, however.

---

### Post by stchman on 2007-05-23
> **skip27 said:**
> I'll post a detailed thread on how to recompile openoffice another time. It's almost 1AM and I have plans, believe it or not. But, I will say this: I think we *might* have a winner.

I've attached two screenshots. The most important compile-time options that I used were --disable-fontooo, --enable-fontconfig and --with-system-freetype (assuming the Turner libraries are installed). You see how *remarkably* close it comes to Abiword, and the differences become even smaller when using other fonts, such as Arial or Times New Roman (see screenshot2.jpg). The fonts do seem a bit fuzzy and faint at times, but I wonder if it's something I can adjust to...

I think we've reached our maximum potential. If my theory is correct, it doesn't seem that we can go any further simply because openoffice.org does not know how to interpret freetype's entire set of font rendering techniques, such as autohinting. I can only *guess* that openoffice.org is equipped with a basic level of interpreting freetype capabilities, meaning that things like a fonts.conf file will have little to no effect. I, personally, was unable to change font rendering in oo.org by adjusting my fonts.conf file. Thus, it seems that a particular font rendering scheme has been defaulted into the code. This is why changing your font rendering from best shapes to best contrast, etc. has no effect.

Anyway, my openoffice.org comprehensive recompiling HOWTO will be posted in a day or two. For the impatient who are already savvy enough with recompiling software, here were the compile-time options I used:

./configure --prefix=/opt/openoffice-2.2.0 --enable-lockdown --disable-fontooo --enable-fontconfig --enable-cups --disable-symbols --disable-debug --disable-dbgutil --enable-gtk --enable-gnome-vfs --enable-evolution2 --enable-build-mozilla --without-fonts --with-system-stdlibs --with-system-freetype --with-jdk-home=/usr/lib/jvm/j2sdk1.4.2 --with-use-shell=bash --with-dict --with-myspell-dicts

NOTE: --with-jdk-home may not apply to your specific system! It is advisable that you use Java 1.4.2, however.

OO2.2 that comes with Feisty has excellent fonts.  Apparently Ubuntu solved the problem.  My fonts in OO2.2 look incredible.  Also if you want to give your Ubuntu that XP fonts look do this:

[http://www.stchman.com/ms_fonts.html](http://www.stchman.com/ms_fonts.html)

I hope this helps.

---

### Post by skip27 on 2007-05-24
Great. I figured everything out. For those of you who are curious as to why OpenOffice.org renders fonts the way it does, read on. After experimenting FOREVER, I have found the solution to all your questions, for certain.

First, I have completely changed my setup. As of now, I have uninstalled the Turner libraries and now use the standard Freetype libraries with FULL LCD subpixel rendering. Here's why:

For one reason or another, OpenOffice.org is *FULLY* compatible ONLY with the Freetype 2.1.10 libraries (libfreetype.so.6.3.8) and versions below that. In Feisty, I'm all but certain that the developers compiled oo.org against these libraries *WITH* the bytecode interpreter enabled, which explains why the fonts are crisp and clean. Now, here's the kicker: you'll notice that fonts in OpenOffice.org using these Freetype libraries render EXACTLY the same way as they would in any other application in Ubuntu using *FULL* LCD subpixel rendering (i.e. NOT medium or slight). Check your Gnome Font settings and make sure that this is what is selected. You'll notice that on LCD panels, you will achieve desktop font rendering uniformity, in that all the fonts look the same across OpenOffice.org and other applications. This is the effect you want, but now you have the explanation as to WHY that's the case.

Second, you might be wondering why other people have complained of blurry fonts under oo.org. Try this. First, you *MUST* be using a version of oo.org that you have either compiled or binaries that you have downloaded from openoffice.org (in RPMs that you have converted to .debs using 'alien') and you must have a version of the Freetype libraries later than 2.1.10; the latest version will do just fine. Do not use oo.org downloaded from the Feisty repo; it will not work. Finally, you must NOT be using the enhanced Turner Freetype libraries; stick to the default Ubuntu ones. Got it? Now, do this in the terminal: export LD_PRELOAD=<path to latest Freetype library>. Then, do 'soffice -writer' and wait for it to load. Notice the blurry fonts? Alright, now do this: Go into the Font Gnome control panel and hit the 'details' button. Leave LCD subpixel rendering turned on under the 'Smoothing' section, but select 'None' under the 'Hinting' section. See how blurry the rest of the fonts are on your system? Notice how it's exactly same as it is in openoffice.org?

What does this mean?

[LIST=1]
[*]We know that OpenOffice.org can be compiled with the bytecode interpreter, but that it MUST be done using a version of Freetype <= 2.1.10 (libfreetype.so.6.3.8). If you want to try this out yourself, download this version from the Freetype website, compile it with the BCI enabled (check ftoption.h), and LD_PRELOAD it before running oo.org.
[*]For some reason, because of the way that Freetype has been revised after 2.1.10, oo.org is simply incapable of processing the changes in these later versions. As a result, it seems that oo.org defaults by disabling hinting ENTIRELY. This is why the fonts appear blurry, which is the same result you get when you go into the Font control panel and disable the hinting. The Feisty developers fixed this by compiling the latest version of oo.org against the Freetype 2.1.10 libraries.
[*]Therefore, compiling the Turner libraries against oo.org is futile, since we won't ever be able to use the hinting to begin with! The Turner libraries did not exist at 2.1.10, so unless he is willing to take that version and modify it, you're stuck with the current 2.1.10 BCI.
[*]However, because the rest of the system *IS* able to understand the changes in the Freetype library, you can continue upgrading these libraries without having to worry about it affecting your other applications. It's just oo.org that cannot process these changes. Nothing about how the BCI functions has changed between 2.1.10 and the current version; it's simply a matter of whether or not an application can "understand" the library it is using, which in this case, happens to be the Freetype library.
[/LIST]

Conclusion? Recompiling OpenOffice.org against anything later than Freetype 2.1.10 is FUTILE and *WILL NOT DO ANYTHING*. Those of you who looked at the screenshots I posted might then ask why I thought I thought I had a winner. The explanation is simple: When I was using that configuration, I was using the Segoe UI font, but with the Turner libraries and with SLIGHT subpixel rendering. Why is this significant? Well, don't forget, there isn't much of a difference between "slight" hinting and "no" hinting. Recall that the oo.org will default to NO hinting when it is linked to a Freetype library > than 2.1.10, and also note that I was using only "slight" hinting for my system. Thus, that explains why my results were so close. It had *nothing* to do with the fact that I had linked oo.org against the Turner libraries, since it was not using hinting in the first place! When openoffice.org is capable of interpreting the changes that have occurred after Freetype 2.1.10, *ONLY THEN* will compiling against the Turner libraries have an effect. Or, you could simply LD_PRELOAD it and it would work just fine (a recompile is not necessary).

So, after all this typing, what's the "optimal" solution?

Stick with the Ubuntu defaults and don't install the MS core fonts. That way, fonts will render uniformly across your entire system, including oo.org. Indeed, so simple, right? But, you don't appreciate the grace and simplicity of a default install until you uncover the technical details of WHY it's better off that way. Now, we have an explanation, and now I can finally put my mind at rest!

For those of you using Edgy (or any other Linux distro for that matter) and complaining of font rendering problems, here is the simple solution (in the terminal): export LD_PRELOAD=<path to libfreetype.so.6.3.8>, and then execute oo.org as usual. Also, you can insert this in the 'soffice' file using so that you don't have to type this up every time. Search the forum for this: you'll find plenty of stuff to read. Or, for the more ambitious, you can recompile oo.org against the Freetype 2.1.10 libraries. Additionally, it may be necessary for you to use the Cairo 1.0.4 (I think that's the right version) libraries with Freetype 2.1.10 to avoid any complications. Make sure you include the Cairo library file in the LD_PRELOAD path if you are encountering problems. Separate it with colons, e.g. export LD_PRELOAD=<path to Freetype>:<path to Cairo>.

---

### Post by hugmenot on 2007-05-24
> **skip27 said:**
> 
Stick with the Ubuntu defaults and don't install the MS core fonts. That way, fonts will render uniformly across your entire system, including oo.org. Indeed, so simple, right? But, you don't appreciate the grace and simplicity of a default install until you uncover the technical details of WHY it's better off that way. Now, we have an explanation, and now I can finally put my mind at rest!

Impressive analysis for a remarkable outcome. I'd rather see OO upstream fix this though.
I actually want to have Turner filtering in OO, too.

---

### Post by skip27 on 2007-05-24
Apparently, Freetype released what are called "rogue patches," and apparently, one of the patches seems to have something to do with getting applications to work properly with the changes starting in Freetype 2.2.0. Presumably, this means that it would also work with versions later than 2.2.0. Information is provided herein:

[http://freetype.sourceforge.net/freetype2/patches/rogue-patches.html](http://freetype.sourceforge.net/freetype2/patches/rogue-patches.html)
[http://freetype.sourceforge.net/freetype2/freetype-2.2.0.html](http://freetype.sourceforge.net/freetype2/freetype-2.2.0.html)

I wonder if we have something here... I'll explore it and post my findings. If we can figure out how to get OpenOffice.org to start recognizing changes in Freetype versions later than 2.1.10, we then have the key to getting the Turner libraries to work with it.

EDIT: Nope, after reading into it, this won't help us. These patches were designed to alleviate problems associated with certain header files that are no longer installed locally following the introduction of Freetype 2.2.0 (Freetype's internal headers). Because oo.org has already fixed this, the rogue patches are of no use. Thus, it seems that font rendering is as good as it's going to get for now.

---

### Post by Juno on 2007-05-24
See this simple trick (It works for me):

Ubuntu Feisty 7.04 | OOo 2.2.0 | LCD monitor | Font rendering: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

---

### Post by skip27 on 2007-05-25
> **Juno said:**
> See this simple trick (It works for me):

Ubuntu Feisty 7.04 | OOo 2.2.0 | LCD monitor | Font rendering: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

Thanks for the post, but I've already tried heavy experimentation with the Turner libraries. Remember: oo.org is partially incompatible with any version of Freetype later than 2.1.10. Also, I noticed that you're either zoomed in quite a bit in your screenshots, or you're simply using a large font. I can guarantee your oo.org looks identical to mine at 100% zoom with 12 pt fonts.

---

### Post by Juno on 2007-05-26
Hi. My solution:

Uninstall font rendering: [http://ubuntuforums.org/showthread.php?p=2716124#post2716124](http://ubuntuforums.org/showthread.php?p=2716124#post2716124)

Enable Smooth fonts: [http://ubuntuforums.org/showpost.php?p=2584327&postcount=140](http://ubuntuforums.org/showpost.php?p=2584327&postcount=140)

Regards.

| Ubuntu Fesity Fawn 7.04 | OO.o 2.2 | LCD 19" |

---

### Post by Juno on 2007-05-26
You need to edit the .fonts.conf file in your home directory. Paste in the xml data below it.

> <?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>

[http://ubuntuforums.org/showpost.php?p=2584327&postcount=140](http://ubuntuforums.org/showpost.php?p=2584327&postcount=140)
[http://ubuntuforums.org/showthread.php?p=16896](http://ubuntuforums.org/showthread.php?p=16896)

---

### Post by H.E. Pennypacker on 2007-06-13
> **skip27 said:**
> 
Second, you might be wondering why other people have complained of blurry fonts under oo.org. Try this. First, you *MUST* be using a version of oo.org that you have either compiled or binaries that you have downloaded from openoffice.org (in RPMs that you have converted to .debs using 'alien') and you must have a version of the Freetype libraries later than 2.1.10; the latest version will do just fine. Do not use oo.org downloaded from the Feisty repo; it will not work. Finally, you must NOT be using the enhanced Turner Freetype libraries; stick to the default Ubuntu ones. Got it? Now, do this in the terminal: export LD_PRELOAD=<path to latest Freetype library>. Then, do 'soffice -writer' and wait for it to load. Notice the blurry fonts? Alright, now do this: Go into the Font Gnome control panel and hit the 'details' button. Leave LCD subpixel rendering turned on under the 'Smoothing' section, but select 'None' under the 'Hinting' section. See how blurry the rest of the fonts are on your system? Notice how it's exactly same as it is in openoffice.org?



Is there a 1-2-3 step guide that will quickly and easily solve the problem, or must I go through re-installing Openoffice, and go through the rest of the guide?  I'd rather go to Preferences, and check off a box that says "Make my fonts look better."  All the other stuff is too much trouble.

---

### Post by LittleCannon on 2007-08-09
There is easy solution. 
On OO forums there is solution for Suse, but it can be used for Ubuntu.

Just unpack attachment in /opt/openoffice.org2.2/program and start OO

Works like a charm

---

### Post by hugmenot on 2007-08-10
Sorry, that didn&#8217;t do anything.
Could you explain why you put the lib into that folder (it doesn&#8217;t exist, but /usr/lib/openoffice/program/ does) and could you post a screenshot of the result?

---

### Post by LittleCannon on 2007-08-10
Here is link with explanation and complete procedure [http://www.oooforum.org/forum/viewtopic.phtml?t=33084&postdays=0&postorder=asc&highlight=fonts&start=75&sid=9c673e6d328601798623c52cb23823b9](http://www.oooforum.org/forum/viewtopic.phtml?t=33084&postdays=0&postorder=asc&highlight=fonts&start=75&sid=9c673e6d328601798623c52cb23823b9)

And here is how my oo looks now

[IMG]http://free-ri.t-com.hr/pepe/pics/oo.jpg[/IMG]

---

### Post by stchman on 2007-11-06
I prefer the look of Ubuntu's fonts over XP's Tahoma fonts.

Here is how OO2.2 in Feisty should look.

[IMG]http://www.stchman.com/images/oo_calc.jpg[/IMG]

---

### Post by hyperair on 2007-12-26
I tried doing that and I had no noticable changes in Hardy. My font rendering in GNOME is subpixel, but what is shown in OOo is the grayscale font rendering.

---

### Post by sicofante on 2008-01-12
Gutsy's font rendering is absolutely gorgeous. It's a shame that OOo screws it all up.

Is there any explanation/solution to this issue? Can we expect this to be fixed in Hardy?

---

### Post by hyperair on 2008-01-13
Um unfortunately not. Perhaps someone should put up a blueprint for this on Launchpad.

---

### Post by sicofante on 2008-01-13
Isn't it weird that the main office app behaves so different from the rest of the system?

---

