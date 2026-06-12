---
title: "staden or other bio-linux software? (amd64)"
date: 2007-05-13
forum: Education &amp; Science
---

### Post by Heliix on 2007-05-13
hello,
I was looking for some GUI software to view and manipulate with DNA sequences and staden package ([http://staden.sourceforge.net/](http://staden.sourceforge.net/)) looked fine. I downloaded and unpacked the source and follow the documentation-but I got stuck at the beginning:
I got these errors:
hela@electra:~/molcell/staden-linux-ia64-1-6-0/linux-ia64-bin$ ./pregap4 
exec: 123: stash: not found
hela@electra:~/molcell/staden-linux-ia64-1-6-0/linux-ia64-bin$ ./stash
bash: ./stash: cannot execute binary file
The ownership and +x flag were OK, sudo had no effect (it gave some gibberish output instead of normal (= readable) error messages).

I gave it up and tried to look up a .deb package of staden or possibly other similar programms, but all I found (on bio-linux home page) were for i386. Can these be installed on amd64 architecture? (Sorry for the stupid question, I guess the answer is 'no'.)

Now, the question is: can anyone give me a hint how to install staden?
Or can you recommend me any other GUI tool to work with DNA/RNA/protein sequences?

thanks.

---

### Post by DrOlaf on 2007-05-16
I had this problem a while ago on my AMD64 machine. I did manage to get the Staden package running under 64-bit Ubuntu by installing a 32-bit environment using a chroot. You can read up on them in this link:

[http://ubuntuforums.org/showthread.php?t=24575]("http://ubuntuforums.org/showthread.php?t=24575")

In the end, however, I had so many other programs like Staden that needed a 32-bit chroot that it was easier just to change back to a 32-bit install. 

Depending on what you want to do, there are some Java-based apps like [Geneious]("http://www.geneious.com/") and [CLC Free Workbench]("http://www.clcbio.com/") but I admit that they don't have the same functionality as Staden.

---

### Post by Heliix on 2007-05-19
that 32-bit chroot was a great advice!! thank you very much :)

---

### Post by u-blunt-2 on 2007-05-23
Dr Olaf : have you tried installing Geneious on amd64 ? I have 64 bit java and I get a blank screen when I try to install their software.

Guess I'm going to have to do my analyses with manual scripts !

---

### Post by macabro22 on 2007-05-24
Geneious and CLCfreeWorkbench seem to show a blank screen when beryl is active. Try enabling metacity instead. (*e.g.* right click your beryl icon on the taskbar and go to "select window manager).

I just downloaded them both. I am not sure yet which is better at it.

---

### Post by DrOlaf on 2007-05-30
> **u-blunt-2 said:**
> Dr Olaf : have you tried installing Geneious on amd64 ? I have 64 bit java and I get a blank screen when I try to install their software.

Guess I'm going to have to do my analyses with manual scripts !

Sorry about the delayed response - I was busy with an NIH grant and I haven't been on here in a few days. I didn't have any problems getting Geneious to install on a 64-bit Feisty installation. I keep a 64-bit partition on my PC to use as a sandbox, and I just installed Geneious v3.0.4 and it worked fine with my 64-bit JVM. I even got two free weeks of Geneious Pro as it was a new installation :)

---

### Post by u-blunt-2 on 2007-08-07
Beryl was the faulty party. It appears Beryl and JAVA don't like each other. I gave geneious a try, however their software had several bugs when dealing with phylogeny and tree/alignment viewing. Switched back to JalView for my sequence comparison needs. 
Also, Jalview is freeware with no Pro licensing, and I have found their developers to be more cooperative and concerned. Only setbacks (imo) are that you cannot scale a tree to its respective alignment and obviously the beryl/JAVA bug. I would expect Geneious to be much better for sharing datasets on LANs, accessing public DBs, and the such.

---

### Post by geneious-developer on 2007-10-22
> **u-blunt-2 said:**
> Beryl was the faulty party. It appears Beryl and JAVA don't like each other. I gave geneious a try, however their software had several bugs when dealing with phylogeny and tree/alignment viewing. Switched back to JalView for my sequence comparison needs. 
Also, Jalview is freeware with no Pro licensing, and I have found their developers to be more cooperative and concerned. Only setbacks (imo) are that you cannot scale a tree to its respective alignment and obviously the beryl/JAVA bug. I would expect Geneious to be much better for sharing datasets on LANs, accessing public DBs, and the such.

Hi,

I'm one of the developers of Geneious. In what way were us developers not sufficiently "cooperative and concerned" when you approached us? (I don't know who you are so I don't know when and in what way you approached us). We have a user forum at [http://www.geneious.com/userforum](http://www.geneious.com/userforum) and we usually respond to any messages there within a few hours - we do take user feedback quite seriously.

Also, can you please be more specific what bugs you encountered in phylogeny and tree / alignment viewing? We are trying our best to make Geneious as bug free as possible, and if there is any bug that we may not be aware of then I'd appreciate if you could let me know. We also have a "Geneious Bugs" category set up in our user forum, where you can submit bug reports.

Tobias (Geneious developer)

---

