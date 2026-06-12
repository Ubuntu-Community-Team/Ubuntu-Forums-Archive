---
title: "Beagle searching within email content"
date: 2009-02-23
forum: General Help
---

### Post by yeleek on 2009-02-23
Hi,

Does anyone have Beagle successfully searching within the content of an email (client being thunderbird) or is it only capable of searching the subject of an email when using Thunderbird?

My experience is that even after having completed a full index, beagle will retrieve an email based on its subject, but not when searching for content from within the same email.

Any thoughts?

Thanks

---

### Post by yeleek on 2009-03-04
Anyone have any thoughts re this pls?

---

### Post by Ron_ on 2009-12-21
[FONT=Verdana]I have been experiencing the same problem.  I am running[/FONT][FONT=Verdana] Thunderbird 2.0.0.23 under Ubuntu 9.10.  The Beagle Indexer extension (*i.e.* the Thunderbird add-on) is version 0.1.3, though it is numbered 0.3.9-3ubuntu1 at Synaptic.

[/FONT]The Thunderbird add-on clearly is writing only header information -- not e-mail content -- to temporary files in .beagle/Indexes/ThunderbirdIndex/ToIndex , where the Beagle daemon picks them up for indexing.

I took a look in /usr/lib/thunderbird/extensions/{b656ef18-fd76-45e6-95cc-8043f26361e7}/chrome/beagle.jar. In that jar, /content/beagleIndexer.js dates back to November 26, 2007 -- around the time of the last major rewrite and version 0.3.0 release. I am no expert in JavaSript, but as far as I can tell, that code was never intended to index anything but the header information (unless code has been removed since then.)

---

### Post by Ron_ on 2009-12-26
I was just informed by one of Beagle's developers that the right place to report this problem is still [http://bugzilla.gnome.org/enter_bug.cgi?product=beagle](http://bugzilla.gnome.org/enter_bug.cgi?product=beagle) .

I've recently tried a couple of things, unsuccessfully, to fix the problem on my own. Make no mistake, this is flailing. I have little understanding of what I am doing, but in the absence of expert support....
1) I downloaded an older copy of the Thunderbird-Beagle add-on, version 0.1.2 . Same problem. Reinstall thunderbird-beagle 0.1.3.
2) I edited the contents of /usr/lib/thunderbird/extensions/{b656ef18-fd76-45e6-95cc-8043f26361e7}/chrome/beagle.jar in the following way:
    a) sudo file-roller
    b) open the file
    c) gedit content/beagleIndexer.js
    d) Based on a discussion I read ( [https://bugzilla.gnome.org/show_bug.cgi?id=530632](https://bugzilla.gnome.org/show_bug.cgi?id=530632) ), describing a possible fix to the extension for Thunderbird 3 *[Note: I am still using TB 2]*, I replaced 3 instances of "path.unixStyleFilePath" with "nativePath" .  Save.  Okay to update the jar.  Close.
e) This produced Exceptions in the Beagle Log that I did not used to have. Basically, it broke the Beagle backend. Reinstall thunderbird-beagle to undo the changes to beagleIndexer.js . Also, delete all files in /home/xxxxx/.beagle/Indexes/ThunderbirdIndex/ToIndex .
f) What we learn from this experience is that Beagle's Index Helper process apparently runs Mono to re-open Thunderbird's folders and read the contents. If this is so, the locus of the main problem (*i.e.*, not indexing e-mail content) is the Beagle backend rather than the Thunderbird add-on. That is a body of code that I dare not touch. It's too bad, though, that the add-on does not just dump the e-mail content while it has the chance.

---

### Post by Ron_ on 2010-04-30
The Beagle community (including Novell) seems unable to offer any further support.  Also, I found no evidence that Canonical has changed its support for desktop search apps since introducing Ubuntu 10.04 yesterday.  So after reviewing all of the information I could find comparing strengths and weaknesses, I shut down the Beagle daemon and installed Recoll.

So far, I am very pleased.  Documentation is good.  Installation was a snap.  Minor customization (e.g., setting a parm to enable Recoll to work with the Firefox Beagle add-on) was easy.  The whole conversion was very uneventful.  Creation of the initial index was reasonably fast (under an hour for about 250,000 files.)  The GUI is clean and clear.  All of the stuff that Beagle caught was there.  And all of the stuff that Beagle missed -- like Thunderbird message content -- showed up.

Compare Recoll news...

    * 2010-01-05 : a 1.13.04 is out. It fixes a nasty bug (broken stemming) in 1.13.02.
    * 2010-01-29 : the full Recoll source repository is now hosted on Bitbucket, along with a Wiki and an issues tracking system. Hopefully, this new channel for reporting bugs and make suggestions will increase the feedback rate...
    * 2010-01-05 : a 1.13.02 is out. It brings some nice improvements and new functions. Please try it and report any problems.
    * 2009-12-10 : 1.12.4 is out. It fixes a problem in the preview window search function (qt4 only).
    * 2008-05-22 : we now have a mailing list:
          o Subscription management
          o Archives

... to Beagle news:
21 Jan 2010      Beagle status: Beagle isn't in active development. It is getting some occasional maintenance done by Novell. 
26 Jan 2009      Beagle 0.3.9 released. 
15 July 2008      Beagle 0.3.8 released. 
7 Jun 2008      Added initial support for indexing removable medium. 
21 May 2008      Added read-only RDF overlay on Beagle index. This RDF store can handle RDF queries and supports different query formats like SPARQL, N3 etc. 
14 May 2008      Kio-beagle ported to KDE4. 

The future is Recoll.

---

