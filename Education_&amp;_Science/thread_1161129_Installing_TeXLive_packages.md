---
title: "Installing TeXLive packages"
date: 2009-05-16
forum: Education &amp; Science
---

### Post by av9765 on 2009-05-16
Hey guys,

I was wondering if someone could help me with the installation of TeXLive packages. I'm very new to ubuntu/linux altogether, but I was running TeXnic Center on Windows just fine. I have installed TeXLive without problem and it seems to be working fine, but (since I didn't install TeXLive-full) I don't even have some basic packages. I have downloaded some .ins files and TeX'd them, but I don't know where to put them. 

Any help is greatly appreciated.

---

### Post by radiocognition on 2009-05-16
If you already are a latex user, then switching over to texlive should not be difficult.  The easiest way to install new packages is to install them in your own user texmf directory.  Usually, texlive is configured to search for user installed local packages in ~/texmf.  You have to manually make the folder.  You can see a copy of my personal texmf folder at this [link]("http://www.prism.gatech.edu/~jmerrill3/FILES/texmf/")

I personally don't like seeing the texmf folder every time I open my home directory.  I usually end up renaming the folder to .texmf (to hide it) and then accordingly adjust the settings in the file /etc/texmf/texmf.d/05TexMF.cnf

Here is a copy of my settings file

```

% original texmf.cnf -- runtime path configuration file for kpathsea.
% (If you change or delete `original' on the previous line, the
% distribution won't install its version over yours.)
% Public domain.
% 
% What follows is a super-summary of what this .cnf file can
% contain. Please read the Kpathsea manual for more information.
% 
% texmf.cnf is generated from texmf.in, by replacing @var@ with the
% value of the Make variable `var', via a sed file texmf.sed, generated
% (once) by kpathsea/Makefile (itself generated from kpathsea/Makefile.in
% by configure).
% 
% Any identifier (sticking to A-Za-z_ for names is safest) can be assigned.
% The `=' (and surrounding spaces) is optional.
% No % or @ in texmf.in, for the sake of autogeneration.
% (However, %'s and @'s can be edited into texmf.cnf or put in envvar values.)
% $foo (or ${foo}) in a value expands to the envvar or cnf value of foo.
% 
% Earlier entries (in the same or another file) override later ones, and
% an environment variable foo overrides any texmf.cnf definition of foo.
% 
% All definitions are read before anything is expanded, so you can use
% variables before they are defined. 
% 
% If a variable assignment is qualified with `.PROGRAM', it is ignored
% unless the current executable (last filename component of argv[0]) is
% named PROGRAM.  This foo.PROGRAM construct is not recognized on the
% right-hand side. For environment variables, use FOO_PROGRAM.
% 
% Which file formats use which paths for searches is described in the
% various programs' and the kpathsea documentation.
% 
% // means to search subdirectories (recursively).
% A leading !! means to look only in the ls-R db, never on the disk.
% A leading/trailing/doubled ; in the paths will be expanded into the
%   compile-time default. Probably not what you want.
% 
% You can use brace notation, for example: /usr/local/{mytex:othertex}
% expands to /usr/local/mytex:/usr/local/othertex.  Instead of the path
% separator you can use a comma: /usr/local/{mytex,othertex} also expands
% to /usr/local/mytex:/usr/local/othertex.  However, the use of the comma
% instead of the path separator is deprecated.
%
% The text above assumes thet path separator is a colon (:).  Non-UNIX
% systems use different path separators, like the semicolon (;).

%  Part 1: Search paths and directories.

% You can set an environment variable to override TEXMF if you're testing
% a new TeX tree, without changing anything else.
% 
% You may wish to use one of the $SELFAUTO... variables here so TeX will
% find where to look dynamically.  See the manual and the definition
% below of TEXMFCNF.

% The tree containing the runtime files closely related to the specific
% program version used:
TEXMFMAIN = /usr/share/texmf

% The main distribution tree:
TEXMFDIST = /usr/share/texmf-texlive

% A place for local additions to a "standard" texmf tree.
% This tree is not used for local configuration maintained by
% texconfig, it uses TEXMFCONFIG below.
TEXMFLOCAL = /usr/local/share/texmf

% TEXMFSYSVAR, where texconfig-sys stores variable runtime data.
% With teTeX-3.0 or later, this must be set.
% For sharing this tree with $TEXMFMAIN:
%   TEXMFSYSVAR = $TEXMFMAIN
% For using a separate tree:
%   TEXMFSYSVAR = /usr/share/texmf-var
TEXMFSYSVAR = /var/lib/texmf

% TEXMFSYSCONFIG, where texconfig-sys stores configuration data.
% With teTeX-3.0 or later, this must be set.
% For sharing this tree with $TEXMFMAIN:
%   TEXMFSYSCONFIG = $TEXMFMAIN
% For using a separate tree:
%   TEXMFSYSCONFIG = /usr/share/texmf-config
TEXMFSYSCONFIG = /etc/texmf

% User texmf trees are allowed as follows.
% This used to be HOMETEXMF.
TEXMFHOME = $HOME/.texmf

% TEXMFVAR, where texconfig stores variable runtime data.
% With teTeX-3.0 or later, this must be set.
% For sharing this tree with $TEXMFMAIN:
%   TEXMFVAR = $TEXMFMAIN
% For using a separate tree:
%   TEXMFVAR = $HOME/.texmf-var  # teTeX 3.0 default
TEXMFVAR = $HOME/.texmf-var

% TEXMFCONFIG, where texconfig stores configuration data.
% With teTeX-3.0 or later, this must be set.
% For sharing this tree with $TEXMFMAIN:
%   TEXMFCONFIG = $TEXMFMAIN
% For using a separate tree:
%   TEXMFCONFIG = $HOME/.texmf-config  # teTeX 3.0 default
% For using a separate tree:
%   TEXMFCONFIG = /usr/share/texmf-config
TEXMFCONFIG = $HOME/.texmf-config

% Now, list all the texmf trees. If you have multiple trees you can
% use shell brace notation, like this:
%   TEXMF = {$TEXMFHOME,!!$TEXMFLOCAL,!!$TEXMFMAIN}
% The braces are necessary.
%
% For texconfig to work properly, TEXMFCONFIG and TEXMFVAR should be named
% explicitly and before all other trees.
TEXMF = {$TEXMFCONFIG,$TEXMFVAR,$TEXMFHOME,$TEXMFSYSCONFIG,!!$TEXMFSYSVAR,!!$TEXMFLOCAL,!!$TEXMFMAIN,!!$TEXMFDIST}

% The system trees.  These are the trees that are shared by all the users.
% If a tree appears in this list, the mktex* scripts will use
% VARTEXFONTS for generated files, if the original tree isn't writable;
% otherwise the current working directory is used.
SYSTEXMF = $TEXMFSYSVAR,$TEXMFLOCAL;$TEXMFMAIN;$TEXMFDIST

% Where generated fonts may be written.  This tree is used when the sources
% were found in a system tree and either that tree wasn't writable, or the
% varfonts feature was enabled in MT_FEATURES in mktex.cnf.
VARTEXFONTS = /tmp/texfonts

% Where to look for ls-R files.  There need not be an ls-R in the
% directories in this path, but if there is one, Kpathsea will use it.
%
% By default, this is only the !! elements of TEXMF, so that mktexlsr
% does not create ls-R files in the non-!! elements -- because if an
% ls-R is present, it will be used, and the disk will not be searched.
% This is arguably a bug in kpathsea, but we will not think about it now.
%
% Historically, Debian has included $TEXMFHOME here, and therefore
% keeps updating its ls-R file.  It is safe to remove it from this list
TEXMFDBS = {!!$TEXMFSYSVAR,!!$TEXMFLOCAL,!!$TEXMFMAIN,!!$TEXMFDIST}

% It may be convenient to define TEXMF like this:
%   TEXMF = {$TEXMFHOME,!!$TEXMFLOCAL,!!$TEXMFMAIN,$HOME}
% which allows users to set up entire texmf trees, and tells TeX to
% look in places like ~/tex and ~/bibtex.  If you do this, define TEXMFDBS
% like this:
%   TEXMFDBS = $TEXMFHOME;$TEXMFLOCAL;$TEXMFMAIN;$VARTEXFONTS
% or mktexlsr will generate an ls-R file for $HOME when called, which is
% rarely desirable.  If you do this you'll want to define SYSTEXMF like
% this:
%   SYSTEXMF = $TEXMFLOCAL;$TEXMFMAIN;$TEXMFDIST
% so that fonts from a user's tree won't escape into the global trees.
%
% On some systems, there will be a system tree which contains all the font
% files that may be created as well as the formats.  For example
%   TEXMFVAR = /var/lib/texmf
% is used on many Linux systems.  In this case, set VARTEXFONTS like this
%   VARTEXFONTS = $TEXMFVAR/fonts
% and do not mention it in TEXMFDBS (but _do_ mention TEXMFVAR).
%
% Remove $VARTEXFONTS from TEXMFDBS if the VARTEXFONTS directory is below
% one of the TEXMF directories (avoids overlapping ls-R files).

```

Note the line where I set the variable TEXMFHOME=$HOME/.texmf
When you are done setting things up and adding new packages, just update the system by running ```
sudo texhash
```

---

### Post by av9765 on 2009-05-16
Thanks a bunch. I definitely see now what you're referring to when you say you don't like seeing texmf in your home directory. I was missing the texhash command. Thanks a lot, I can tell you how much of a headache you saved me...

---

### Post by gnwiii on 2009-05-17
It is worth noting that TeX Live 2008 can be installed from CTAN.  This gets current
versions of packages which can be installed or removed using the new tlpkg package manager.  There aren't yet debian/Ubuntu packages, but the CTAN version installs into
a single directory.  If you don't use the option to create symlinks in /usr/bin, it
can coexist with Ubuntu's tex live 2007 -- you choose which version to use by adjusting the PATH variable.

---

### Post by Pelops on 2009-07-15
Since I use a lot of personal packages and custom commands, and I have to work with Ubuntu, Mac and Windows, I store my latex packages into a folder of my removable HD.  I wonder if there's a way to add that folder to the path of TexLive, as an addiction of $HOME/texmf (which I'm forced to use as well), so when I have to work with Ubuntu I don't need to copy my files into $HOME/texmf.

Thank you in advance.

---

### Post by Tibuda on 2009-07-15
> **Pelops said:**
> Since I use a lot of personal packages and custom commands, and I have to work with Ubuntu, Mac and Windows, I store my latex packages into a folder of my removable HD.  I wonder if there's a way to add that folder to the path of TexLive, as an addiction of $HOME/texmf (which I'm forced to use as well), so when I have to work with Ubuntu I don't need to copy my files into $HOME/texmf.

Thank you in advance.

Try a symbolic link.
```
ln -sf /media/removablehd/texmf $HOME/texmf
```

---

### Post by unutbu on 2009-07-15
I believe, after following danielrmt's advice, you may also need to run
```

mktexlsr
```
(See for example, [http://ubuntuforums.org/showpost.php?p=7445038&postcount=6](http://ubuntuforums.org/showpost.php?p=7445038&postcount=6)).

---

### Post by Pelops on 2009-07-17
> **danielrmt said:**
> Try a symbolic link.
```
ln -sf /media/removablehd/texmf $HOME/texmf
```

danielrmt's tip is good: I linked all the subfolders of /media/removable/texmf/tex/latex to $HOME/texmf
 
 e.g.
 
```
 ln -sf /media/removablehd/texmf/tex/latex/mypackage $HOME/texmf/tex/latex/
```
 
 and then
 
```
 sudo texhash
```
 
 Thank you very much.

---

### Post by PGScooter on 2009-07-17
instead of changing the name of texmf, you could just add it to a .hidden file in that directory.

---

### Post by Pelops on 2009-07-17
> **PGScooter said:**
> instead of changing the name of texmf, you could just add it to a .hidden file in that directory.

Could you be more explicit? Do you mean something like:

```
ln -sf /media/removablehd/texmf/tex/ $HOME/texmf/.tex
```

I tried it as my first option, but it didn't work.

---

### Post by PGScooter on 2009-07-17
Pelops,

Sorry, I should have been more specific. I was replying to radiocognition. He hides a folder by prefixing a ".". This is a perfectly valid way of hiding something, but I find that when there are links involved it is better to create a file called ".hidden" in that folder and in .hidden you can just put a list of the names of files and folders you want to be treated as hidden. I don't know if this only works for certain programs, but it has worked great for me.

---

### Post by Irenimus on 2009-07-27
Hello all.

I too am a newcomer to Ubuntu, but have been a user of LaTeX on windows previously. 

I am trying to install a couple of rather recent packages (namely siunitx and graphicxsp) using MiKTeX and have successfully installed them to /home/<user>/miktex-texmf/. I used radiocognition's hint to change the $TEXMFHOME line in 05TeXMF.cnf file to $HOME/miktex-texmf. Unfortunately, after 'texhash'ing it, my editor (Kile) still doesn't detect the presence of siunitx...

Any hints or suggestions would be greatly appreciated.

Thanks!

---

### Post by Irenimus on 2009-07-27
I think I just figured it out for myself....

sudo update-texmf

after editing 05TeXMF.cnf and before 'sudo texhash'.

Any further advice would still be gratefully received!

---

### Post by kozimodo on 2009-07-28
You can put everything in /home/<user>/texmf instead of miktex-texmf and everything should just work (mv miktex-texmf texmf).  I've never had to run update-texmf.

---

### Post by koend on 2009-08-04
[FONT=Verdana]Thanks Kozimodo! I had the same problem as Irenimus and your suggestion helped to solve it. Wonderful!

However, each time I now install a new package with mpm, it creates a new /home/<user>/miktex-texmf directory again after which I need to manually merge it with /home/<user>/texmf.

I compiled mpm without the -DMIKTEX_INSTALLROOT and -DMIKTEX_ROOTS options (As was done on [http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/](http://texblog.net/latex-archive/linux/mpm-miktex-package-manager/) for example), so perhaps that explains it.. but is there a way to still change this location afterwards? I thought running [/FONT]> sudo mpm --install-root=~/texmf --update-db[FONT=Verdana] would do the trick (as I found on [http://dojo.miktex.org/blogs/christian_schenk/articles/mpmunix.aspx](http://dojo.miktex.org/blogs/christian_schenk/articles/mpmunix.aspx)), but unfortunately not.

Any ideas? Thanks!

Koen.
[/FONT]

---

### Post by kozimodo on 2009-08-04
If you previously changed the line 05TeXMF.cnf to 'TEXMFHOME = $HOME/miktex-texmf' then you need to change it back to 'TEXMFHOME = $HOME/texmf'.

---

### Post by koend on 2009-08-06
I've check that and everything looks ok. And Kile finds my newly installed packages, so I'm happy.

It's just that mpm hasn't realised I moved the files (no real surprise) and I don't know how to tell Miktex to install new packages in ~/texmf from now on. When I run 'sudo mpm --update-db' now, a new ~/miktex-texmf directory is created.. is there a Miktex config file somewhere? The file in /var/lib/miktex-texmf/miktex/config does not contain any reference to ~/miktex-texmf...

---

### Post by kozimodo on 2009-08-06
I don't use mpm myself so I'm not sure what I can tell you.  From what I can see, the big advantage of mpm is that it can install packages on the fly.  But TeXLive should include all of them anyway so why not install texlive-full (unless you're really tight on HD space).

---

