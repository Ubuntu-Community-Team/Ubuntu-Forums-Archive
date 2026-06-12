---
title: "emacs-snapshot?"
date: 2005-10-17
forum: Closed Requests
---

### Post by shidai.liu on 2005-10-17
Personally, I love emacs-snapshort very much. I even installed a version from Debian unstable. Please vote for this app to include in ubuntu.

---

### Post by Jengu on 2005-10-22
What's the difference from normal emacs?

---

### Post by shidai.liu on 2005-10-22
[QUOTE=Jengu]What's the difference from normal emacs?[/QUOTE]
Here's the change log

emacs-snapshot (1:20051007-1) unstable; urgency=low

  * New snapshot:
    + BibTeX mode now honors `sentence-end-double-space' and other filling
      variables, thanks to Roland Winkler (closes: #330917).
    + Autoloads in cua-base and ibuf-ext no longer explicitely request the
      .el file (closes: #332315).
    + Includes Speedbar version 1.0.

  * debian/patches/tmp-build-fix.dpatch: Temporary patch reverting
    unimportant changes that break the emacs-nox build.
  * debian/patches/00list: Update.

 -- Romain Francoise <rfrancoise@debian.org>  Fri,  7 Oct 2005 15:41:44 +0200

emacs-snapshot (1:20050929-1) unstable; urgency=low

  * The "Dittsche" release.

  * New snapshot.

 -- Romain Francoise <rfrancoise@debian.org>  Thu, 29 Sep 2005 08:52:15 +0200

emacs-snapshot (1:20050922-1) unstable; urgency=low

  * New snapshot.

 -- Romain Francoise <rfrancoise@debian.org>  Thu, 22 Sep 2005 08:23:16 +0200

emacs-snapshot (1:20050918-1) unstable; urgency=low

  * New snapshot.

  * Add linda overrides, bringing the override support level with lintian.
    + debian/*.overrides: Rename to debian/*.overrides.lintian.
    + debian/emacs-bin-common.overrides.linda: New file.
    + debian/emacs-common.overrides.linda: Ditto.
    + debian/emacs-el.overrides.linda: Ditto.
    + debian/emacs.overrides.linda: Ditto.

  * debian/patches/debian-version-mention.dpatch: Fix patch description to
    mention emacs-version and not version as the function modified.

  * debian/rules:
    + Update lintian override filenames.
    + Install linda overrides.
    + Remove useless '--with-gif' confflag.

 -- Romain Francoise <rfrancoise@debian.org>  Sun, 18 Sep 2005 15:33:30 +0200

emacs-snapshot (1:20050908-1) unstable; urgency=low

  * New snapshot.

  * debian/rules: Compress all files in emacs-el.

 -- Romain Francoise <rfrancoise@debian.org>  Thu,  8 Sep 2005 18:33:23 +0200

emacs-snapshot (1:20050901-1) unstable; urgency=low

  * New snapshot.

  * debian/patches/debian-rpath.dpatch: New file, disables RPATH in
    emacs-x and emacs-gtk binaries.
  * debian/patches/00list: Update.

  * debian/emacs-bin-common.overrides: Add overrides for man pages
    installed as alternatives: their section is correct, and the binaries
    do have man pages.

  * debian/emacs-common.overrides: Add override for the "wrong name for
    upstream changelog" check: it's a directory, and it holds the (many)
    upstream changelogs (and the top-level changelog is now symlinked,
    too).

  * debian/rules:
    + Strip the dpatch-list-patch header line.
    + Symlink upstream top-level changelog.
    + Swap fixed and variable parts in changelog file names.

  * debian/patches/debian-cssc-vc-backend.dpatch: Add "Provided by" line.
  * debian/patches/debian-font-lock-tty.dpatch: Ditto.
  * debian/patches/debian-licenses-location.dpatch: Ditto.
  * debian/patches/debian-vc-bfn.dpatch: Ditto.
  * debian/patches/debian-version-mention.dpatch: Ditto.

 -- Romain Francoise <rfrancoise@debian.org>  Thu,  1 Sep 2005 18:25:51 +0200

emacs-snapshot (1:20050825-1) unstable; urgency=low

  * New snapshot.

  * debian/emacs-bin-common.prerm: Fix buggy loop left over from
    pre-unstable packaging, because of this no alternatives were actually
    removed when emacs-bin-common was removed... (closes: #324870).

  * debian/emacs-bin-common.postinst:
    + In emacs-snapshot, the binary named 'emacs' is moved out of the way
      before expanding @ALTERNATIVES@ so it doesn't appear in the list.
      Don't special-case for it in emacs-bin-common.postinst as it'll never
      be there.
    + Remove unused INFOFILES variable.

  * debian/rules:
    + Add upstream changelogs in /usr/share/doc so that users can have
      access to them without downloading 30M of sources.  It doesn't make
      much difference in a package that occupies more than 50M and has some
      real value for users since emacs-snapshot is a constantly moving
      target.
    + Don't install menu items for emacs-nox.

  * debian/patches/debian-licenses-location.dpatch: New patch, modifies
    `describe-copying' to find the full text of the GPL in the system-wide
    location for licenses (/usr/share/common-licenses), the COPYING file
    included in the Emacs distribution isn't installed (and differs from
    the Debian version in whitespace only).

  * New versioning scheme: the overly large version number in previous
    uploads triggered a bug in quinn-diff which resulted in emacs-snapshot
    not appearing in q-d output and thus not being rebuilt on some archs.
    The bug has been fixed in quinn-diff (thanks to Ryan Murray) but to
    prevent any further damage, I'm changing the versioning scheme to
    something sane (and mandated by Policy, see §3.2.1).
    The historical versioning scheme was of doubtful value anyway.

  * debian/changelog: Delete trailing whitespace in pre-unstable entries.

 -- Romain Francoise <rfrancoise@debian.org>  Thu, 25 Aug 2005 18:35:13 +0200

emacs-snapshot (20050819140000-1) unstable; urgency=low

  * New snapshot.

  * debian/rules: README.Debian is generated from the list of Debian
    patches and its size varies depending on the number of patches, so
    dh_compress sometimes compresses it, and sometimes not.  To avoid
    having to fix the references in debian/copyright and NEWS, forcibly
    leave it uncompressed.

  * debian/patches/image-pbm-xbm.dpatch: Dropped (fixed upstream).
  * debian/patches/00list: Update.

 -- Romain Francoise <rfrancoise@debian.org>  Fri, 19 Aug 2005 18:34:53 +0200

emacs-snapshot (20050812140000-2) unstable; urgency=low

  * debian/patches/image-pbm-xbm.dpatch: New file, revert an upstream
    change that erroneously removes the pbm and xbm image types.
  * debian/patches/00list: Update.

 -- Romain Francoise <rfrancoise@debian.org>  Fri, 12 Aug 2005 20:00:22 +0200

emacs-snapshot (20050812140000-1) unstable; urgency=low

  * New snapshot:
    + Fixes a bug triggered by GTK+ 2.6.9 where opened menus could
      disappear randomly in emacs-snapshot-gtk (closes: #322307).
    + Includes Tramp 2.0.50.

  * debian/patches/debian-emacs-news.dpatch: Fix reference to
    README.Debian, it isn't compressed automatically in emacs-snapshot
    (it's now installed by dh_installdocs).

  * debian/changelog:
    + Fix name of NEWS file in previous entry.
    + Add mode to the local variables section.

  * debian/rules:
    + Set pkg_name for emacs-common and emacs-bin-common to fix the
      generation of lintian override files.
    + Set flavour description.
    + Pipe dpatch-list-patch output to sed to generate outline compliant
      headings, the outline regexp used in the emacs21 packages doesn't
      match in emacs-snapshot, and it's simpler to have regular outline
      sections in the file in the first place.

  * debian/copyright.in:
    + Use the new FSF postal address (updated in COPYING in the Emacs
      sources).
    + Add 2005 to copyright years.
    + Fix location of README.Debian.
  * debian/copyright: Regenerate.

  * debian/patches/debian-font-lock-tty.dpatch: Add outline markers.
  * debian/patches/debian-vc-bfn.dpatch: Ditto.

  * debian/patches/debian-cssc-vc-backend.dpatch: Add dpatch description
    marker (caused an empty patch description in README.Debian).

  * debian/control.in: Add flavour description to the short description of
    the main package, which is emacs-snapshot in this source package
    (closes: #322180).
  * debian/control: Regenerate.

  * debian/README.in:
    + Add information section stolen from the initial NEWS entry.
    + Remove paragraph about .elc files and Leim being added to the
      upstream sources: these packages are built from a snapshot tarball for
      which neither of these things is true.
    + Remove local variables section.
    + Add note about the baz archive.

  * debian/emacs.menu.in: Add -i option to the menu command item in order
    to get the Emacs icon in the GNOME window list (and equivalent
    features in other desktop environments).
  * debian/emacs.desktop: Ditto.

 -- Romain Francoise <rfrancoise@debian.org>  Fri, 12 Aug 2005 17:51:10 +0200

emacs-snapshot (20050805100000-1) unstable; urgency=low

  * Initial snapshot release in unstable.  See NEWS.Debian.gz for general
    information on these packages.

  * debian/control.in:
    + Set myself as Maintainer, Jerome and Rob as Uploaders.
    + Bump dpatch build-dependency to dpatch (>= 2.0.9).
    + Bump Standards-Version to 3.6.2, no changes needed.
    + Fix Replaces line on emacs21.
  * debian/control: Regenerate.

  * debian/rules:
    + Add -Wno-pointer-sign to CFLAGS.
    + Generate debian/README.Debian from the templates.

  * debian/NEWS: New file.

  * debian/patches/debian-font-lock-tty.dpatch: New file.
  * debian/patches/debian-vc-bfn.dpatch: New file.
  * debian/patches/00list: Update.

  * Several other minor changes, see the baz log.

 -- Romain Francoise <rfrancoise@debian.org>  Fri,  5 Aug 2005 14:41:18 +0200

emacs-snapshot (20050519215621-1) unstable; urgency=low

  * New snapshot release.

  * Do not force epaths re-generation after calls to configure any more
    since configure now provides a '--enable-locallisppath'
    - debian/rules:
      + Add --enable-locallisppath option to confflags
      + Remove epaths_force_cmd function
      + Remove calls to epaths_force_cmd

 -- Jerome Marant <jerome@debian.org>  Thu, 19 May 2005 22:07:33 +0200

emacs-snapshot (20050425220908-2) unstable; urgency=low

  * Merge fixes from Davide Salvetti <salve@debian.org>
    - debian/patches/misc-unseparated.dpatch: Remove hunks.

  * Incorporated fixes from Daniel Brockman <daniel@brockman.se>:
    - debian/rules:
      + Don't prefix local_lpath paths with EMACS_COMMON
      + Add new epaths_force_cmd
      + Add calls to epaths_force_cmd after every call to configure
      + Add new variable local_lpath_install which prefixes all
        paths from local_lpath with EMACS_COMMON
      + Set locallisppath to local_lpath_install at install-time

 -- Jerome Marant <jerome@debian.org>  Thu, 12 May 2005 21:57:05 +0200

emacs-snapshot (20050425220908-1) unstable; urgency=low

  * New snapshot release.

  * Merge changes from 21.4a-1

  * debian/control:
    - Switch Maintainer and Uploaders fields.
    - Build-depend on dpatch >= 2.0.9.

  * debian/rules: properly install emacs-snapshot-nox manpage.

  * debian/patches/misc-unseparated.dpatch:
    - Fix docstring for message-sendmail-f-is-evil: the first line of a
      docstring should be a complete sentence describing the function.
      Thanks to Kai Großjohann <kai@emptydomain.de>
    - Updated patch to etc/NEWS.

 -- Jerome Marant <jerome@debian.org>  Mon, 25 Apr 2005 22:37:09 +0200

emacs-snapshot (20040508-1) unstable; urgency=low

  * Initial release. This package is branched from emacs21 21.3+1-5.

  * Port package to debhelper [Jérôme Marant]
    - debian/control.in: added debhelper to build-dependencies.
    - debian/control: regenerated.
    - debian/rules
    - debian/build-binary-pkg: removed.
    - debian/compat: new file containing debhelper compatibility version.
    - debian/docs: new file.
    - debian/emacs-common.docs: new file. 

  * Add GTK+ 2.x support (#179469, #194388) [Jérôme Marant]
    - debian/control.in: add new package emacs-gtk
    - debian/control: regenerated.
    - debian/rules

  * Remove upstream applied patches [Jérôme Marant]
    - debian/patches/scroll-margin.dpatch
    - debian/patches/save-buffer.dpatch
    - debian/patches/hurd-libio-glibc.dpatch
    - debian/patches/detect-coding-iso2022.dpatch
    - debian/patches/browse-url.dpatch
    - debian/patches/battery-acpi-support.dpatch

 -- Jerome Marant <jerome@debian.org>  Sat,  8 May 2004 14:42:33 +0200

Local Variables:
coding: utf-8
mode: debian-changelog
End:

---

### Post by realwhz on 2005-11-06
I'm looking forward to this package too :p

---

### Post by Technoviking on 2005-11-08
I have made instructions here, but please use with caution:
[http://ubuntuforums.org/showthread.php?p=476487#post476487](http://ubuntuforums.org/showthread.php?p=476487#post476487)

Mike

---

### Post by Technoviking on 2005-11-09
I will not be submitting my emacs-snapshot package to the offical backports since it is built from the Debian Unstable source and not Dapper source.

Mike

---

### Post by shidai.liu on 2005-11-10
You could also propose emacs-snapshot to be included in dapperdrake

---

### Post by Technoviking on 2005-11-11
emacs-snapshot has been added to Dapper, approved for backport.

Mike

---

### Post by jdong on 2005-11-12
Done deal.

---

### Post by shidai.liu on 2005-11-15
[QUOTE=jdong]Done deal.[/QUOTE]

Is it available? I can't see it.

---

### Post by Manny C on 2005-11-21
Definitely available in Dapper. You should look for the package emacs-snapshot.

---

### Post by shidai.liu on 2005-11-21
Yep. but it breaks a lot of packages in Breezy. But there is a backport for breezy anyway.

---

