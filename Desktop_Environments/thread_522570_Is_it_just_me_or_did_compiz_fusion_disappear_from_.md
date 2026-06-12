---
title: "Is it just me or did compiz fusion disappear from tervino's repos?"
date: 2007-08-10
forum: Desktop Environments
---

### Post by djrobthaman on 2007-08-10
????

Had to reinstall ubuntu so I added trev's repo's, like I've done so many times before and I can't find any compiz fusion binaries.  What happened?

---

### Post by dougfractal on 2007-08-10
Seems fine to me
[http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/)

but looking at the time on some files "11-Apr-2007 01:04"  It looks like he was uploading.

---

### Post by djrobthaman on 2007-08-10
Yeah.  It does look fine doesn't it.  According to [this web page]("http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/index.html") all the necessary files are there.  But I don't see any of them.

Also, [this how-to]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion") that, up to less than a week ago, used trev's repos has now been changed to use another.  and on page 58 of that how-to post, somebody asks about slow updates to the repo (I know, the files should still be there anyway).  

But would there be any reason that even after I added the gpg key and updated my repo lists that there could be files present on a repo that I couldn't see?

---

### Post by dougfractal on 2007-08-10
the files info is in the packages.gz  If it's not in that then apt-get won't take it.

firefox and Gdebi will. Just hunt them down and install manually (click it)

The thing about bleeding edge and auto svn/git snapshots is you are going to get some bad days. After all its work in progress.  It'll be alright tommorrow.

---

### Post by djrobthaman on 2007-08-10
I guess I'll do that.  I got another version of fusion from a different repo and it's nowhere near as good as trevino's (I didn't think it would be an issue... go figure).

But do you know if when I install it manually, it would automatically update if I still had the repo in my list?

---

### Post by djrobthaman on 2007-08-10
What the hell is wrong with me????

I need to label cds correctly.  I installed the 64bit ubuntu when I meant to install the 32 bit.  So all the wonderful 32 bit packages that were in the eyecandy repo were invisible to me.  And I didn't add the 64 bit because I didn't realize that's what I had.

Oh well, thanks for the help.  If you hadn't suggested installing the files manually I probably wouldn't have figured it out :)

---

