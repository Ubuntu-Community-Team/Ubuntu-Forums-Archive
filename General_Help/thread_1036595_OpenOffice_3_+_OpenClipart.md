---
title: "OpenOffice 3 + OpenClipart"
date: 2009-01-11
forum: General Help
---

### Post by aptgetmoo on 2009-01-11
Hi

I used to have openclipart inside my openoffice 2.4. But after I installed the openoffice.org 3 package from this [ppa]("https://launchpad.net/~openoffice-pkgs"), I cannot access openclipart from the gallery. How do I configure openoffice 3 to load openclipart again?

I ran ```
sudo dpkg-reconfigure openclipart
``` which didn't seem to fix it.

---

### Post by ricardisimo on 2009-02-13
I've installed OOo 3.01, and uninstalled 2.4. Now it appears that I cannot install openclipart without reinstalling 2.4 all over again. I'd like to avoid that if possible.

---

### Post by aptgetmoo on 2009-02-13
If you reinstall OOo 2.4 and openclipart, and after that install OOo3, can you use the openclipart?

---

### Post by ricardisimo on 2009-02-13
Are you asking if version 3.0 can access openclipart? As I recall, yes, but I'd like to avoid reinstalling everything all over again.

---

### Post by johnjohn2 on 2009-02-13
> **ricardisimo said:**
> are you asking if version 3.0 can access openclipart? As i recall, yes, but i'd like to avoid reinstalling everything all over again.

lovely wanted to know this as well

---

### Post by aptgetmoo on 2009-02-13
> **ricardisimo said:**
> Are you asking if version 3.0 can access openclipart? As I recall, yes, but I'd like to avoid reinstalling everything all over again.

Oh. Then why don't you just reinstall openclipart?

---

### Post by ricardisimo on 2009-02-14
That was how this post started... I'd have to reinstall OOo 2.4 as well, and I'd like to avoid that, now that I have 3.0 working just the way I like it.

---

### Post by FraggedLocust on 2009-02-18
I have the same problem. Installing 500Mb of packages I don't necessarily need is something I'd like to avoid.

---

### Post by ricardisimo on 2009-02-18
Well, I think this is a step in the right direction... just not for a quasi-newb like myself:
Openclipart.org has a [tarball for download]("http://openclipart.org/downloads/0.18/openclipart-0.18-full.tar.gz") that I have already extracted into my home folder. Theoretically, I should be able to navigate the terminal to the resulting folder, "openclipart-0.18-full", and then simply run
```
make install
```
and have all of the tagged svgs and pngs installed in /usr/share/clipart.

The only problem is that this doesn't work. Other than that we're great. Here's what I got:
```
~/Computer Files/TAR/openclipart-0.18-full$ make install
sed -e "s/APP_VERSION/0.18/" \
		nsis/build.nsi.in > nsis/build.nsi.tmp
sed -e "s/FULL_NAME/Open Clip Art Library/" \
		nsis/build.nsi.tmp > nsis/build.nsi.tmp2
sed -e "s/SHORT_NAME/openclipart/" \
		nsis/build.nsi.tmp2 > nsis/build.nsi.tmp3
sed -e "s/NSISDIR/nsis/" \
		nsis/build.nsi.tmp3 > nsis/build.nsi
# clean up tmp files
rm -Rf nsis/build.nsi.tmp*
/bin/install -c -m 755 -d /usr/local/share/clipart/openclipart
make: /bin/install: Command not found
make: *** [install] Error 127
```
Any help would be greatly appreciated. Thanks in advance.

---

### Post by ricardisimo on 2009-02-19
No one has installed OpenClipart this way?

---

### Post by ricardisimo on 2009-02-20
How about if I post the install instructions that came with the download? Here it is:
> Open Clip Art Library Package Install
=====================================

This is the basic install package for all of the packages that the Open Clip 
Art Library (OCAL) builds on the monthly releases. This will eventually be 
supplanted, but is very necessary at present as OCAL is growing to that point.

To basically build all these packages, to install clipart onto your syste, or
to build the win32 installer, please read below.

To install the clipart into your system:

	make install

To install the clipart not into the default, /usr/share/clipart, then do this:

	CLIPARTDIR=/PATH/TO/clipart make install


Packages
--------

Make sure that the latest clipart is installed into the folder:

	clipart

Make sure that the latest tools (which are usually in the CVS module 
clipart_web/tools) are copied as is to:

	tools

In order to build the win32 installer, go to [http://nsis.sf.net](http://nsis.sf.net) to get the 
source package linux installer. Version 2.08 works great at the time of this
writing. It is set by default to be at:

	/opt/nsis

If this needs to be changed, then one can do this:

	MAKENSIS=/PATH/TO/makensis make nsis

Now, once all these pieces are in place:

	make dist

This builds all packages into the folder:

	packages


To clean all build files and dists:

	make distclean

To build the win32 package, which IS NOT built with make dist, due to the 
strange nature of the nsis install:

	make nsis

This places the win32 installer into the packages folder as well.

In order to build the RPMs, one must have rpmbuild. On gentoo, I just emerge 
rpm and get rpmbuild and other scripts that are necessary in making RPM 
packages. RPMs are built automatically with make dist.
One thing that confuses me somewhat is how often apps that need compiling come with RPM instructions... considering how much more, well, ubiquitous Ubuntu is, you'd think debian instructions would be the rule and not the exception, wouldn't you?

Any sort of help with this would be greatly appreciated. Thanks.

---

### Post by Macchiavelli on 2009-03-19
Hi,

i solved it for me: After installation of Openoffice 3, i installed openclipart-openoffice.org from 

[COLOR=RoyalBlue] Download: [http://packages.ubuntu.com/de/intrepid/openclipart-openoffice.org](http://packages.ubuntu.com/de/intrepid/openclipart-openoffice.org)[/COLOR]

then i installed it. It installs himself the cliparts (ca. 112 MB).

Then i copied the files from 
[I]
/usr/lib/openoffice/share/gallery/[/I]

to 

*/home/XXXXX/.openoffice.org/3/user/gallery*

where XXXXX stands for my username.

After starting of openoffice the Gallery works fine.

Greetings

Macchiavelli

---

### Post by Macchiavelli on 2009-03-19
Ok, this solution isn't the smart one, because it had to be done for every user, but it works without compiling ;)

Macchiavelli

---

### Post by Macchiavelli on 2009-03-19
If someone has a better solution please tell!

Macciavelli

---

### Post by Macchiavelli on 2009-03-19
Sorry, i wanted to post this entry somewere else.How can i delete this entry?

---

### Post by reecehart on 2009-04-01
I had the same problem.  Here's a fairly easy, per-user solution:

After installing openclipart-openoffice.org, I did
$ dpkg-query -L openclipart-openoffice.org
Note the many files in /usr/lib/openoffice/share/gallery/. You should see the same thing.

In OpenOffice 3, go to Tools > Options. Click Paths in the left panel, then Gallery in the right. Click Edit.  Add a new path '/usr/lib/openoffice/share/gallery' .  After a few clicks of OK to accept the changes, you're done.

This was all done on 09.04 (Jaunty) beta.

-Reece

---

### Post by freesitebuilder on 2009-04-26
thanks, reecehart - the solution from the OO forum was to do a reinstall of 9.04!

NB: This needs a restart of OO to make the changes show up.

---

### Post by ricardisimo on 2009-10-06
> **reecehart said:**
> I had the same problem.  Here's a fairly easy, per-user solution:

After installing openclipart-openoffice.org, I did
$ dpkg-query -L openclipart-openoffice.org
Note the many files in /usr/lib/openoffice/share/gallery/. You should see the same thing.

In OpenOffice 3, go to Tools > Options. Click Paths in the left panel, then Gallery in the right. Click Edit.  Add a new path '/usr/lib/openoffice/share/gallery' .  After a few clicks of OK to accept the changes, you're done.

This was all done on 09.04 (Jaunty) beta.

-Reece

I'm assuming you mean "/usr/share/openclipart", or no?

---

### Post by ricardisimo on 2009-10-06
No, you were right! I did have to select the new directory as the default, however. Did no one else?

---

### Post by claracc on 2009-10-13
The solution pointed by Machiavelli works for me. Thanks
 
The other one, the one where you add the path /usr/lib/openoffice/share/gallery to the tools-->options--> route, gallery doesn't work, openoffice doesn't add the new themes to gallery.

Any other working solution?

Greetings, Clara

---

### Post by claracc on 2009-10-13
Sorry, the other solution, the one adding the path /usr/lib/.openofice/share/gallery in tools, options, route, gallery also works. I was putting a wrong path.
Now, i have the gallery working doing this workaround.

Thanks

---

