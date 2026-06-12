---
title: "So, what's the deal with Ubuntu and /opt?"
date: 2009-05-12
forum: General Help
---

### Post by stathol on 2009-05-12
I'm pretty much a newcomer to Linux, and seeing as I don't (well, *didn't*) have a very good grasp on the filesystem organization in *nix, I've been reading through the FHS (2.3) docs. ...Hey, it seemed like a good idea at the time :P

I think I've got a pretty good handle on it now. I.e., I get the distinction between the /usr hierarchy and the the /usr/local hierarchy. I also think I generally understand the purpose of /opt, but there's something that I don't quite grok about the way Ubuntu organizes its files. I dug through some old threads here pertaining to /opt, but didn't really come across  any clear explanation.

Namely, when you install "self-contained" packages (ex. Firefox), they wind up in /usr/lib/<package>, of all places. Why there, and not /opt/<package>? If I understand the HFS, this seems like the logical place for that type of package to go. Distribution-installed software is *allowed* to go in /opt as long as it doesn't screw with locally installed software already present there. Does Ubuntu eschew /opt just to avoid that potential conflict, or what?

If so, I can understand why they wouldn't want to use /opt. But then...why choose /usr/lib as the alternative? Just no place better to go? Typically, very few of the files in /usr/lib/<package> are actually libraries. This doesn't really bother me, I just find it kind of odd. Does anyone know the rationale, here? How do other common distributions handle this situation? My only prior linux experience was with SUSE nearly 10 years ago, and I don't remember anything about where it kept files :)

---

### Post by mb_webguy on 2009-05-12
The /opt directory is similar in use to the /usr/local (not /usr/lib) directory.  Generally, software installed to the /opt directory is fairly self contained and not very dependent on external libraries.  Software in /usr/local only really differs from software in /usr in that it was installed locally, such as by compiling from source, rather than through a package manager.  Software in the /opt directory is also installed locally, but generally through a binary installer or script.

In my experience, whether an installer puts an application in /usr/local or /opt is a bit arbitrary.

---

### Post by stathol on 2009-05-12
Heh. Yeah, I get the difference between /usr and /usr/local, but that wasn't a typo. Firefox really *does* get installed to /usr/**lib**, not /usr/local. That's why it seems weird to me.

Verbatim dump from my terminal:
```
stathol@raimi:/$ ls -l /usr/bin/firefox*
lrwxrwxrwx 1 root root 11 2009-05-02 20:35 /usr/bin/firefox -> firefox-3.0
lrwxrwxrwx 1 root root 32 2009-05-02 20:35 /usr/bin/firefox-3.0 -> ../lib/firefox-3.0.10/firefox.sh
stathol@raimi:/$ ls -l /usr/lib/firefox-3.0.10/
total 84
lrwxrwxrwx 1 root root     7 2009-05-02 20:35 abrowser -> firefox
lrwxrwxrwx 1 root root     7 2009-05-02 20:35 abrowser-3.0 -> firefox
-rw-r--r-- 1 root root  2026 2009-04-25 18:36 application.ini
-rw-r--r-- 1 root root  2067 2009-04-25 18:34 blocklist.xml
-rw-r--r-- 1 root root    49 2009-04-25 18:34 browserconfig.properties
drwxr-xr-x 3 root root  4096 2009-05-02 20:35 chrome
drwxr-xr-x 2 root root  4096 2009-05-02 20:35 components
drwxr-xr-x 3 root root    52 2009-05-01 02:32 defaults
lrwxrwxrwx 1 root root    25 2009-05-01 02:32 dictionaries -> ../../share/myspell/dicts
drwxr-xr-x 2 root root    29 2009-05-02 20:35 distribution
lrwxrwxrwx 1 root root    28 2009-05-01 02:32 extensions -> ../firefox-addons/extensions
-rwxr-xr-x 1 root root  9644 2009-04-25 18:36 ffox-3-beta-profile-migration-dialog
-rwxr-xr-x 1 root root 30232 2009-04-25 18:36 firefox
lrwxrwxrwx 1 root root     7 2009-05-02 20:35 firefox-3.0 -> firefox
-rw-r--r-- 1 root root   456 2009-04-25 18:33 firefox-3.0-restart-required.update-notifier
-rwxr-xr-x 1 root root  4006 2009-04-25 18:33 firefox.sh
drwxr-xr-x 2 root root    86 2009-05-02 20:35 icons
drwxr-xr-x 2 root root    28 2009-05-02 20:35 modules
lrwxrwxrwx 1 root root    25 2009-05-01 02:32 plugins -> ../firefox-addons/plugins
-rwxr-xr-x 1 root root 11410 2009-04-25 18:34 run-mozilla.sh
lrwxrwxrwx 1 root root    31 2009-05-01 02:32 searchplugins -> ../firefox-addons/searchplugins

```

As you can see, /usr/bin/firefox ultimately points to a shell script in /usr/lib/firefox/. The actual binaries are in there, too, along with a lot of other stuff that definitely doesn't qualify as a library (ex. all the icons in /usr/lib/firefox/icons/).

I thought maybe firefox was just the odd duck here, but it looks like there are quite a few other packages that are set up that way. Try running:

```
ls -l /usr/bin /usr/sbin | grep ../lib
```

Poking around in the referenced directories in /usr/lib reveals quite a bit of non-library content being installed there. There are also some isolated examples that don't have symlinks from any of the bin or sbin directories. Vino-server, for instance.

That's basically what I'm asking about -- why is all this stuff getting installed to /usr/lib? That doesn't seem quite...right.

---

### Post by mb_webguy on 2009-05-17
/usr/lib is for software libraries -- extra software not part of the executable (which would be in /usr/bin) but required by it, and which isn't merely data user by the executable (which would be in /usr/share).  If you do "whereis firefox", you'll see that Firefox is installed to /usr -- with the executable in /usr/bin, the libraries in /usr/lib, and the data files to /usr/share.

---

