---
title: "vi editor, no auto code completion for c structure only"
date: 2009-05-24
forum: General Help
---

### Post by colau on 2009-05-24
Hi,
Auto code completion is working with vi editor but it is not working for C language structure.
After dot(.) the variables do not appear as list.
I followed this link.
[http://vim.wikia.com/wiki/VimTip1608](http://vim.wikia.com/wiki/VimTip1608)
Screenshot is attached.
Does anyone have the solution for this?

---

### Post by cmnorton on 2009-05-25
Which vim is installed? There are slight behavior differences between tiny and full vim. I've re-installed full vim on 8.04, but it has an annoying affect with my Informix tools. I'll live with it to get the full blown version. 

Check to see what is installed.

---

### Post by colau on 2009-05-25
> **cmnorton said:**
> Which vim is installed? There are slight behavior differences between tiny and full vim. I've re-installed full vim on 8.04, but it has an annoying affect with my Informix tools. I'll live with it to get the full blown version. 

Check to see what is installed.
```

dpkg -l | grep vim

```
```

ii  vim                                        2:7.2.079-1ubuntu5                   Vi IMproved - enhanced vi editor
ii  vim-common                                 2:7.2.079-1ubuntu5                   Vi IMproved - Common files
ii  vim-dbg                                    2:7.2.079-1ubuntu5                   Vi IMproved - enhanced vi editor (debugging symbols)
ii  vim-doc                                    2:7.2.079-1ubuntu5                   Vi IMproved - HTML documentation
ii  vim-full                                   2:7.2.079-1ubuntu5                   Vi IMproved - enhanced vi editor (transitional package)
ii  vim-gnome                                  2:7.2.079-1ubuntu5                   Vi IMproved - enhanced vi editor - with GNOME2 GUI
ii  vim-gui-common                             2:7.2.079-1ubuntu5                   Vi IMproved - Common GUI files
ii  vim-runtime                                2:7.2.079-1ubuntu5                   Vi IMproved - Runtime files
ii  vim-tiny                                   2:7.2.079-1ubuntu5                   Vi IMproved - enhanced vi editor - compact version

```

```

apt-get show vim

```
```

Package: vim
Priority: optional
Section: editors
Installed-Size: 1668
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian VIM Maintainers <pkg-vim-maintainers@lists.alioth.debian.org>
Architecture: i386
Version: 2:7.2.079-1ubuntu5
Replaces: vim-common (<< 1:7.1-175+1)
Provides: editor
Depends: vim-common (= 2:7.2.079-1ubuntu5), vim-runtime (= 2:7.2.079-1ubuntu5), libacl1 (>= 2.2.11-1), libc6 (>= 2.4), libgpm2 (>= 1.20.4), libncurses5 (>= 5.6+20071006-3), libpython2.6 (>= 2.6), libselinux1 (>= 2.0.59)
Suggests: ctags, vim-doc, vim-scripts
Conflicts: vim-common (<< 1:7.1-175+1)
Filename: pool/main/v/vim/vim_7.2.079-1ubuntu5_i386.deb
Size: 853774
MD5sum: 071b95abc2df958c8b1bbbfc2a5d8edb
SHA1: 719f13df12d351756d8ac9ce213fae7d7a881bfc
SHA256: d312564e2b9bdca60e4983656f72b9901afa46a3f83379da96d858e39e7b2484
Description: Vi IMproved - enhanced vi editor
 Vim is an almost compatible version of the UNIX editor Vi.
 .
 Many new features have been added: multi level undo, syntax
 highlighting, command line history, on-line help, filename
 completion, block operations, folding, Unicode support, etc.
 .
 This package contains a version of vim compiled with a rather
 standard set of features.  This package does not provide a GUI
 version of Vim.  See the other vim-* packages if you need more
 (or less).
Homepage: [http://www.vim.org/](http://www.vim.org/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
Task: server

```

---

### Post by cmnorton on 2009-05-27
There's stuff at [http://vim.wika.com]("http://vim.wika.com/") and [http://www.vim.org/](http://www.vim.org/) as well.

---

