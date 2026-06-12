---
title: "How to replace e2fsprogs with newest version?"
date: 2009-05-22
forum: General Help
---

### Post by logos34 on 2009-05-22
8.04 Heron is still using 1.40.8. I want to compile the latest version 1.41.5.

When I try to uninstall the current version, it give me a dire warning.  Can I safely uninstall anyway and replace it with new version as long as i don't reboot in between?

---

### Post by Uzi304 on 2009-05-22
Yeah it should be fine if you uninstall and then compile and install the later version before a reboot. I'm 80% sure so you might wanna wait for confirmation.

---

### Post by VMC on 2009-05-22
> **logos34 said:**
> 8.04 Heron is still using 1.40.8. I want to compile the latest version 1.41.5.

When I try to uninstall the current version, it give me a dire warning.  Can I safely uninstall anyway and replace it with new version as long as i don't reboot in between?

Here's a rather old topic that appears to be on the same lines as what your requesting. Hopefully it hels:
[http://www.linuxquestions.org/questions/debian-26/e2fsprogs-blocking-apt-get-362194/](http://www.linuxquestions.org/questions/debian-26/e2fsprogs-blocking-apt-get-362194/)

---

### Post by logos34 on 2009-05-23
ok, thanks guys. 

> **VMC said:**
> Here's a rather old topic that appears to be on the same lines as what your requesting. Hopefully it hels:
[http://www.linuxquestions.org/questions/debian-26/e2fsprogs-blocking-apt-get-362194/](http://www.linuxquestions.org/questions/debian-26/e2fsprogs-blocking-apt-get-362194/)

[Post #4 ]("http://www.linuxquestions.org/questions/showthread.php?p=1869960#post1869960")in that link gives me courage...seems to support what uzi304 says.

So I may try it.  Besides, if it goes awry I have a clone of /, so I can restore.

Here's what I was getting (really tries to scare you):

> $ sudo apt-get remove e2fsprogs
[sudo] password for logos34: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper librsvg2-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apparmor apparmor-utils bootchart e2fsprogs initscripts system-services ubuntu-minimal upstart-compat-sysv
[COLOR="Red"]WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs[/COLOR]
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
After this operation, 6808kB disk space will be freed.
[COLOR="Red"]You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'[/COLOR]

Looks like the chian of dependencies is this:

apparmor -> upstart-compat-sysv -> initscript -> **e2fsprogs (>= 1.32+1.33-WIP-2003.04.14-1)**

so initscript depends on e2fsprogs version newer than 1.32.  Hope vers, 1.41 works

---

### Post by logos34 on 2009-05-23
I used sudo checkinstall as last step but it fails to make a deb pkg.  Just refuses...some error about /usr/sbin/uuid (?), not sure exactly...anyway, I'm not going to do it unless it makea a deb.  So back to regular version...

---

### Post by cmost on 2009-05-23
I wouldn't use Checkinstall to make your debs.  Its sort of hackish.  Try the following to make an honest to goodness DEB that you can keep or share:

1.  Create a working folder for e2fsprogs.  Change to the working folder for ; open a gnome-terminal, and issue the command: sudo apt-get source e2fsprogs.  If you're using your own source tarball, simply unpack it and then change to that directory.
2. Grab all the dependencies needed to rebuild e2fsprogs. Issue this command: sudo apt-get build-dep e2fsprogs
3. Apply patches to the source directory, if desired, or make other changes as you might want or need. Obviously only YOU know what you want to do and it's up to you to figure out specifically how to do it for the particular package you're rebuilding.  If no changes, simply move to the next step.
4. Rebuild a new deb for installation. Within the source directory issue the command: sudo debuild -us -uc
5. Now if you look in the parent directory you should find a brand new, recompiled DEB file ready for installation.
6. Install the new DEB file by changing to the parent directory and issuing the command: sudo dpkg -i *.deb
7. To ensure Apt (or Synaptic) doesn't "upgrade" your custom deb with the stock version available in the repositories, you can PIN the package in /etc/apt/preferences file. Pinning the packages in the preferences file ensures that both Apt AND Synaptic respect your preferences. Using Synaptic's GUI pinning interface only affects Synaptic and not Apt at the command line. Use Gedit to open this file as root: sudo gedit /etc/apt/preferences. Copy the following lines into this file (modify for your package name):

Package: e2fsprogs
Pin: version 1.41.5*
Pin-Priority: 1001

The Pin-Priority of 1001 ensures that Apt NEVER upgrades your Debs with another version.

Good luck!

---

### Post by logos34 on 2009-05-23
thanks for the comments!

I'll definitely look into using debuild/devscripts as an alternative

I've used checkinstall for years now...aside from occasional build failure (like today) its served me well...A lot of people use it. 

Why isn't debuild user more?

---

### Post by mc4man on 2009-05-23
I generally always try build to debian packages whenever possible, particularly when there's multiple packages involved as there is in this case.

You'll probably need to update your debhelper for hardy, look in backports

(as to whether there is any advantage to installing the latest set of e2fsprogs packages in hardy can't say.

Note: if your building in home dir. you can lose the sudo for debuild

---

### Post by logos34 on 2009-05-23
mc4man:

use debuild a lot?  I was just reading up on it [here]("http://www.linux.com/archive/feature/60383?theme=print") (or is there a better howto?

---

### Post by mc4man on 2009-05-23
> use debuild a lot

I use debuild, fakeroot debian/rules binary, occasionally checkinstall and for some sources, just make install. (vlc i tend to just use make install.

I think you just try to look at your source, why your building and see what's the best approach, with best in some cases being just what's easiest.

Some sources will have a debian dir., others you'll need to create one or apply a debian .diff to the source. For others just a configure, make, make install (or possibly checkinstall) is more suitable.   What's more important for debian packages is making sure the rules, control, confflags, changelog are created or edited if need be to suit your purpose or install.

As is typical in linux there are usually multiple ways to get to the same point, so it's just a matter what your looking to do and finding a way to do it.

For instance in my latest hardy I took some jaunty sources, applied the jaunty diff, then edited the appropriate files in the debian dir. so it would work as I wished in hardy.
I'm sure there were other ways, but it was easy, clean and gave me what I wanted.

The opposite of that was I decided I liked the idea of having the full path in the nautilus title bar window and also when minimized.
In that case, because it was just a source edit, the repo source was fine, so an apt-get source and fakeroot.... did the trick. (another case of multiple packages (5) where checkinstall would most likely be unsuitable

That link appears to have some good info, I'm going to read it myself, always something to learn


Edit:
anyway if you build your e2.... the screen shows what you'll get.

I'd probably split off all the -dev and dbg packages before doing a dpkg -i ... First you may not want or need them and -dev packages can sometimes cause trouble when done in bulk with dpkg (*.deb), if any of them have outside dependencies.
( generally easier to install -devs afterwards individually with Gdebi

Also note I'm not inclined to install them. (stuff like this I'd be inclined to test on a 'throwaway' install first

---

### Post by logos34 on 2009-05-24
where is a good howto/step-by-step explanation and guide to using debuild?

I'm strking out...only managed to one successful build out of four tries, and then it failed to install.

---

### Post by cmost on 2009-05-24
I use debuild all the time and rarely run into snags.  What type of errors are you experiencing?

In the meantime, check out this great source:
"Rolling your own Debian packages"
Part 1
[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336)
Part 2
[http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

---

### Post by logos34 on 2009-05-24
I saw page2 already...There are hardly any guides, really surprising, I expected to find gobs...I should clarify: it usually builds the deb but I get a some (or a lot) of errors and warnings at the end...I'll post an example later

---

### Post by logos34 on 2009-05-25
> **cmost said:**
> I use debuild all the time and rarely run into snags.  What type of errors are you experiencing?
ok, example:

I want to comile the latest version of [usbview (version  1.1)]("http://linux.softpedia.com/progDownload/USBView-Download-46015.html").

First I check:
> 
$ sudo apt-get build-dep usbview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

Then, following page2 of the guide above:

> $ dh_make -n -s -e [email]logos34@sbcglobal.net[/email]
Maintainer name : logos34
Email-Address   : [email]logos34@sbcglobal.net[/email] 
Date            : Mon, 25 May 2009 15:36:13 -0500
Package Name    : usbview
Version         : 1.1
License         : gpl
Type of Package : Single
Hit <enter> to confirm: y
Done. Please edit the files in the debian/ subdirectory now. usbview

Edit control:

> Source: usbview
Section: [COLOR="Red"]utilities[/COLOR]
Priority: extra
Maintainer: logos34 <logos34@sbcglobal.net>
Build-Depends: debhelper (>= 5), autotools-dev
Standards-Version: 3.7.2

Package: usbview
Architecture: [COLOR="Red"]amd64[/COLOR]
Depends: ${shlibs:Depends}, ${misc:Depends}
Description:  [COLOR="Red"]A GTK+ program that displays the topography of the devices that are plugged into the USB [/COLOR]
bus

so far so good.  now:


> $ fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/logos34/downloads/usbview-1.1'
[COLOR="Red"]make[1]: *** No rule to make target `distclean'.  Stop.[/COLOR]
make[1]: Leaving directory `/home/logos34/downloads/usbview-1.1'
[COLOR="Red"]make: [clean] Error 2 (ignored)[/COLOR]
rm -f config.sub config.guess
dh_clean 

Why the error?  'rules' file shows this:

> clean:
        dh_testdir
        dh_testroot
        rm -f build-stamp 

        # Add here commands to clean up after the build process.
        [COLOR="Red"]-$(MAKE) distclean[/COLOR]
        rm -f config.sub config.guess

        dh_clean

The second test, /debian/rules build looks ok, but with the binary test I get this:
> 
$ fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean -k 
dh_installdirs
# Add here commands to install the package into debian/usbview.
/usr/bin/make DESTDIR=/home/logos34/downloads/usbview-1.1/debian/usbview install
make[1]: Entering directory `/home/logos34/downloads/usbview-1.1'
make[2]: Entering directory `/home/logos34/downloads/usbview-1.1'
test -z "/usr/local/bin" || /bin/mkdir -p "/home/logos34/downloads/usbview-1.1/debian/usbview/usr/local/bin"
  /usr/bin/install -c 'usbview' '/home/logos34/downloads/usbview-1.1/debian/usbview/usr/local/bin/usbview'
test -z "/usr/local/share/man/man8" || /bin/mkdir -p "/home/logos34/downloads/usbview-1.1/debian/usbview/usr/local/share/man/man8"
 /usr/bin/install -c -m 644 'usbview.8' '/home/logos34/downloads/usbview-1.1/debian/usbview/usr/local/share/man/man8/usbview.8'
make[2]: Leaving directory `/home/logos34/downloads/usbview-1.1'
make[1]: Leaving directory `/home/logos34/downloads/usbview-1.1'
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
dh_installexamples
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
[COLOR="Red"]dpkg-shlibdeps: error: syntax error in debian/control at line 12: line with unknown format (not field-colon-value)
dh_shlibdeps: command returned error code 2304
make: *** [binary-arch] Error 1[/COLOR]

?

Ok, skip it, let's try debuild:

> $ debuild -us -uc
[COLOR="Red"]dpkg-checkbuilddeps: error: syntax error in debian/control at line 12: line with unknown format (not field-colon-value)
debuild: fatal error at line 993:
You do not appear to have all build dependencies properly met, aborting.
(Use -d flag to override.)[/COLOR]
If you have the pbuilder package installed you can run
/usr/lib/pbuilder/pbuilder-satisfydepends as root to install the
required packages, or you can do it manually using dpkg or apt using
the error messages just above this message.

EDIT:

it was a line-break at line 12 causing the prob...just backspaced and now fine...BUT why did the unmet dependencies warning go away?  

Despite the warnings and errors at end (mostly minor stuff i didn't bother with), I guess it was a success (about time). Right?

> $ debuild -us -uc
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/logos34/downloads/usbview-1.1'
test -z "usbview" || rm -f usbview
rm -f *.o
rm -f *.tab.c
test -z "" || rm -f 
rm -f config.h stamp-h1
rm -f TAGS ID GTAGS GRTAGS GSYMS GPATH tags
rm -f config.status config.cache config.log configure.lineno config.status.lineno
rm -rf ./.deps
rm -f Makefile
make[1]: Leaving directory `/home/logos34/downloads/usbview-1.1'
rm -f config.sub config.guess
dh_clean 
 dpkg-source -b usbview-1.1
dpkg-source: building usbview in usbview_1.1.tar.gz
dpkg-source: building usbview in usbview_1.1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info CFLAGS="" LDFLAGS="-Wl,-z,defs"
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for x86_64-linux-gnu-gcc... x86_64-linux-gnu-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether x86_64-linux-gnu-gcc accepts -g... yes
checking for x86_64-linux-gnu-gcc option to accept ISO C89... none needed
checking dependency style of x86_64-linux-gnu-gcc... gcc3
checking for library containing strerror... none required
checking for x86_64-linux-gnu-gcc... (cached) x86_64-linux-gnu-gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether x86_64-linux-gnu-gcc accepts -g... (cached) yes
checking for x86_64-linux-gnu-gcc option to accept ISO C89... (cached) none needed
checking dependency style of x86_64-linux-gnu-gcc... (cached) gcc3
checking for x86_64-linux-gnu-gcc... (cached) x86_64-linux-gnu-gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether x86_64-linux-gnu-gcc accepts -g... (cached) yes
checking for x86_64-linux-gnu-gcc option to accept ISO C89... (cached) none needed
checking dependency style of x86_64-linux-gnu-gcc... (cached) gcc3
checking how to run the C preprocessor... x86_64-linux-gnu-gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for x86_64-linux-gnu-pkg-config... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/logos34/downloads/usbview-1.1'
/usr/bin/make  all-am
make[2]: Entering directory `/home/logos34/downloads/usbview-1.1'
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
mv -f .deps/main.Tpo .deps/main.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT interface.o -MD -MP -MF .deps/interface.Tpo -c -o interface.o interface.c
mv -f .deps/interface.Tpo .deps/interface.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT callbacks.o -MD -MP -MF .deps/callbacks.Tpo -c -o callbacks.o callbacks.c
mv -f .deps/callbacks.Tpo .deps/callbacks.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT usbtree.o -MD -MP -MF .deps/usbtree.Tpo -c -o usbtree.o usbtree.c
usbtree.c: In function &#8216;SelectItem&#8217;:
usbtree.c:214: warning: cast from pointer to integer of different size
usbtree.c: In function &#8216;DisplayDevice&#8217;:
usbtree.c:236: warning: cast to pointer from integer of different size
mv -f .deps/usbtree.Tpo .deps/usbtree.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT showmessage.o -MD -MP -MF .deps/showmessage.Tpo -c -o showmessage.o showmessage.c
mv -f .deps/showmessage.Tpo .deps/showmessage.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT usbparse.o -MD -MP -MF .deps/usbparse.Tpo -c -o usbparse.o usbparse.c
mv -f .deps/usbparse.Tpo .deps/usbparse.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT configure-dialog.o -MD -MP -MF .deps/configure-dialog.Tpo -c -o configure-dialog.o configure-dialog.c
mv -f .deps/configure-dialog.Tpo .deps/configure-dialog.Po
x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1        -Wall -MT about-dialog.o -MD -MP -MF .deps/about-dialog.Tpo -c -o about-dialog.o about-dialog.c
mv -f .deps/about-dialog.Tpo .deps/about-dialog.Po
x86_64-linux-gnu-gcc  -Wall  -Wl,-z,defs -o usbview main.o interface.o callbacks.o usbtree.o showmessage.o usbparse.o configure-dialog.o about-dialog.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0    
make[2]: Leaving directory `/home/logos34/downloads/usbview-1.1'
make[1]: Leaving directory `/home/logos34/downloads/usbview-1.1'
#docbook-to-man debian/usbview.sgml > usbview.1
touch build-stamp
 fakeroot debian/rules binary
dh_testdir
dh_testroot
dh_clean -k 
dh_installdirs
# Add here commands to install the package into debian/usbview.
/usr/bin/make DESTDIR=/home/logos34/downloads/usbview-1.1/debian/usbview install
make[1]: Entering directory `/home/logos34/downloads/usbview-1.1'
make[2]: Entering directory `/home/logos34/downloads/usbview-1.1'
test -z "/usr/bin" || /bin/mkdir -p "/home/logos34/downloads/usbview-1.1/debian/usbview/usr/bin"
  /usr/bin/install -c 'usbview' '/home/logos34/downloads/usbview-1.1/debian/usbview/usr/bin/usbview'
test -z "/usr/share/man/man8" || /bin/mkdir -p "/home/logos34/downloads/usbview-1.1/debian/usbview/usr/share/man/man8"
 /usr/bin/install -c -m 644 'usbview.8' '/home/logos34/downloads/usbview-1.1/debian/usbview/usr/share/man/man8/usbview.8'
make[2]: Leaving directory `/home/logos34/downloads/usbview-1.1'
make[1]: Leaving directory `/home/logos34/downloads/usbview-1.1'
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
dh_installexamples
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
[COLOR="Red"]dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libatk-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libm.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libpangocairo-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libpango-1.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libcairo.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libgmodule-2.0.so.0 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/usbview/usr/bin/usbview shouldn't be linked with libdl.so.2 (it uses none of its symbols).[/COLOR]
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_builddeb
dpkg-deb: building package `usbview' in `../usbview_1.1_amd64.deb'.
 dpkg-genchanges
dpkg-genchanges: including full source code in upload
dpkg-buildpackage (debuild emulation): full upload; Debian-native package (full source is included)
Now running lintian...
W: usbview source: debian-rules-ignores-make-clean-error line 48
W: usbview source: out-of-date-standards-version 3.7.2 (current is 3.7.3)
W: usbview source: maintainer-not-full-name logos34
W: usbview: package-contains-empty-directory usr/sbin/
W: usbview: copyright-lists-upstream-authors-with-dh_make-boilerplate
W: usbview: copyright-contains-dh_make-todo-boilerplate
W: usbview: copyright-without-copyright-notice
E: usbview: description-too-long
E: usbview: extended-description-is-empty
W: usbview: maintainer-not-full-name logos34
W: usbview: unknown-section utilities
Finished running lintian.



---

### Post by mc4man on 2009-05-25
I wouldn't worry too much about those shlibdeps warnings.
for the control it's just a few things that don't matter too much, this would be a bit better

> Source: usbview
Section: x11
Priority: optional
Maintainer: Doug Whatever <logos34@sbcglobal.net>
Build-Depends: debhelper (>= 7), autotools-dev
Standards-Version: 3.7.3
Homepage: 

Package: usbview
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: Usb device viewer
 A GTK+ program that displays the topography of the 
 devices that are plugged into the USB bus ( just used debuild on a modded vlc for jaunty  - worked great

---

### Post by logos34 on 2009-05-25
thanks.

From now on I think I'll try debuild instead of make install if checkinistall fails the deb pkg build step.  It's not like I'm a dev sharing debs out of a ppa launchpad account, so I really don't see the need to get fancy.

---

### Post by cmost on 2009-05-29
In case anyone is interested, I just read an article about this nifty new graphical tool for easily creating DEBs in Gnome!  Check it out!  I tried it and it works wonderfully!

[http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/](http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/)

---

### Post by logos34 on 2009-05-29
> **cmost said:**
> In case anyone is interested, I just read an article about this nifty new graphical tool for easily creating DEBs in Gnome!  Check it out!  I tried it and it works wonderfully!

[http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/](http://www.stefanoforenza.com/giftwrap-helps-you-create-debs/)

looks interesting...but no deb for 8.04 :(

I tried the source, but it doesn't respond to ./configure (? maybe it's corrupt--one guy had a md5sum mismatch)

---

### Post by cmost on 2009-05-29
Just for giggles, did you try the 8.10 deb?

---

### Post by logos34 on 2009-05-29
> **cmost said:**
> Just for giggles, did you try the 8.10 deb?

yes, which not surprisingly complained about unsatisfiable dependencies

---

### Post by HerCsD on 2009-07-22
Personally,I downloaded the source code and installed the newer version "onto" the older one.Installed some dependencies and voila.Partition manager could now create an ext4 filesystem.I am not sure if this the "correct" way but it worked for me.

Note:If you use kernel version < 2.6  and glibc < 2.2 the author suggests configuring with ./configure --disable-tls.Check INSTALL and README if you download the source code.

---

