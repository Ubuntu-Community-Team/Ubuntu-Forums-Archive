---
title: "Beagle refuses to index chats, emails, rss, etc."
date: 2009-12-09
forum: Desktop Environments
---

### Post by wmgoree on 2009-12-09
On karmic, Beagle 0.3.9

beagle-index-info yields:

> Index information:
Name: KonqBookmark
Count: 0
Crawling: False

Name: manpages
Count: 4242
Crawling: False

Name: applications
Count: 212
Crawling: False

Name: IndexingService
Count: 0
Crawling: False

Name: Labyrinth
Count: 0
Crawling: False

Name: EvolutionDataServer
Count: 0
Crawling: False

Name: Blam
Count: 0
Crawling: False

Name: Files
Count: 3373
Crawling: False

Name: Thunderbird
Count: 0
Crawling: False

Name: KAddressBook
Count: 0
Crawling: False

Name: Konversation
Count: 0
Crawling: False

Name: Akregator
Count: 0
Crawling: False

Name: KNotes
Count: 0
Crawling: False

Name: NautilusMetadata
Count: -1
Crawling: False

Name: Tomboy
Count: 0
Crawling: False

Name: EvolutionMail
Count: 0
Crawling: False

Name: Pidgin
Count: 0
Crawling: False

Name: Kopete
Count: 0
Crawling: False

Name: KOrganizer
Count: 0
Crawling: False

Name: KMail
Count: 0
Crawling: False

Name: documentation
Count: 27408
Crawling: False

Name: KonquerorHistory
Count: 0
Crawling: False

Name: Empathy
Count: 0
Crawling: False

Name: Liferea
Count: 0
Crawling: False

Name: Opera
Count: 0
Crawling: False

Name: GMailSearch
Count: -1
Crawling: FalseEvery backend is enabled in beagle-settings. the xml files in ~/.beagle/config say that no backend is denied and that my home directory is to be indexed (and the files in my home directory are being indexed, just not any of the other backends: empathy, evo, liferea, etc.). Am I missing something obvious? 

Editing to add: I have the filesystem mounted with xattr like the FAQ suggests, but my home folder is mounted as encryptfs; could that screw beagle up?

Anybody know a good way to figure out where the problem is? Thanks!

---

### Post by Ron_ on 2009-12-22
I am sorry to see that no one has responded yet, and my reply is unlikely to help much.  I have my home directory in an encrypted ext4 partition, and I am not experiencing the same problem as you are with Beagle's backend.

I wonder, though, whether ext4 vs ext3 makes any difference.  I have seen no discussion of Beagle's ability/inability to take advantage of extended attributes in ext4.

I am having a problem with another part of Beagle -- the Thunderbird add-on.  That component clearly is writing only header information -- not e-mail content -- to  temporary files in .beagle/Indexes/ThunderbirdIndex/ToIndex , where the Beagle daemon picks them up for indexing.

I took a look in /usr/lib/thunderbird/extensions/{b656ef18-fd76-45e6-95cc-8043f26361e7}/chrome/beagle.jar.  In that jar, /content/beagleIndexer.js dates back to November 26, 2007 -- around the time of the last major rewrite and version 0.3.0 release.  I am no expert in JavaSript, but as far as I can tell, that code was never intended to index anything but the header information (unless code has been removed since then.)  The Beagle-project web site might be accused of false advertising, but I wonder how much of the information there predates the rewrite. 

I am running Thunderbird 2.0.0.23 under Ubuntu 9.10.  The Thunderbird-Beagle Indexer extension is 0.1.3, though Synaptic numbers it 0.3.9-3ubuntu1.

Thunderbird 3.0, which is now available, boasts many improvements -- you can judge for yourself -- but it may not be compatible with the current add-on.  This portends bad tidings unless someone steps Beagle support up a notch.

---

### Post by Ron_ on 2009-12-26
I was just informed by one of Beagle's developers that the right place to report this problem is still [http://bugzilla.gnome.org/enter_bug.cgi?product=beagle](http://bugzilla.gnome.org/enter_bug.cgi?product=beagle) .

I've recently tried a couple of things, unsuccessfully, to fix the problem on my own.  Make no mistake, this is flailing.  I have little understanding of what I am doing, but in the absence of expert support....
1) I downloaded an older copy of the Thunderbird-Beagle add-on, version 0.1.2 .  Same problem.  Reinstall thunderbird-beagle 0.1.3.
2) I edited the contents of  /usr/lib/thunderbird/extensions/{b656ef18-fd76-45e6-95cc-8043f26361e7}/chrome/beagle.jar in the following way:
    a) sudo file-roller
    b) open the file
    c) gedit content/beagleIndexer.js
    d) Based on a discussion I read ( [https://bugzilla.gnome.org/show_bug.cgi?id=530632](https://bugzilla.gnome.org/show_bug.cgi?id=530632) ), describing a possible fix to the extension for Thunderbird 3 *[Note: I am still using TB 2]*, I replaced 3 instances of "path.unixStyleFilePath" with "nativePath" .  Save.  Okay to update the jar.  Close.
    e) This produced Exceptions in the Beagle Log that I did not used to have.  Basically, it broke the Beagle backend.  Reinstall thunderbird-beagle to undo the changes to beagleIndexer.js .  Also, delete all files in /home/xxxxx/.beagle/Indexes/ThunderbirdIndex/ToIndex .
    f)  What we learn from this experience is that Beagle's Index Helper process apparently runs Mono to re-open Thunderbird's folders and read the contents.  If this is so, the locus of the main problem (*i.e.*, not indexing e-mail content) is the Beagle backend rather than the Thunderbird add-on.  That is a body of code that I dare not touch.  It's too bad, though, that the add-on does not just dump the e-mail content while it has the chance.

---

### Post by Ron_ on 2010-01-04
I've done a little more digging, in case anyone else cares to jump in.  Source code for the Beagle Thunderbird backend is here: [http://vbox4.gnome.org/browse/beagle/tree/beagled/ThunderbirdQueryable/ThunderbirdQueryable.cs?h=beagle-tbird-soc07](http://vbox4.gnome.org/browse/beagle/tree/beagled/ThunderbirdQueryable/ThunderbirdQueryable.cs?h=beagle-tbird-soc07) . The action seems to be around lines 343-347 (called from lines 381-383 and carried forward at line 398.) A partial explanation of what is going on can be found here: [http://beagle-project.org/Filter_Tutorial](http://beagle-project.org/Filter_Tutorial) . (See the section "DoOpen() and DoClose().") As I understand it, the file is just a big buffer. Mail messages are laid end-to-end in the file, so the only way to retrieve a particular message is to specify its offset postion and its size. This stream is handed off to parser.ConstructMessage, etc.
 I am hoping that some reader will have enough experience to spot a potential weakness with respect to Ubuntu 9.X, AMD64, etc.

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

