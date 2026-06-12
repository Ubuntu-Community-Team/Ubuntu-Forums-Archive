---
title: "Converting LaTeX files to OpenOffice: LyX, tex4ht, and oolatex woes"
date: 2007-05-24
forum: Education &amp; Science
---

### Post by tholy on 2007-05-24
Hi,

I recently learned that LyX has an option to export to OpenDoc format, which is useful because one can then convert scientific manuscripts to a format (like .doc) that biology journals will typically accept. It seems that many LaTeX and LyX users prefer this approach as being more robust than latex2rtf. Internally, the conversion uses a program called oolatex; on other distributions, converting to OpenOffice format is an option that one can find on the File->Export menu of LyX.

I think there are quite possibly some problems either with my machine, or there are packaging issues in (K)ubuntu. Observations:
1. apt-cache search for oolatex in Feisty does not yield any hits. It's part of the tex4ht package, which is "advertised" in the package database as being for conversion to HTML but in fact is useful for many types of conversion, including to OpenOffice.
2. The executables in the tex4ht path are in /usr/share/tex4ht and do not end up on the user's path.
3. To get the "OpenOffice.org Writer" export option to show up in LyX, here's what you have to do:
       PATH=$PATH:/usr/share/tex4ht; export PATH
       lyx
       Now, within LyX select Tools->Reconfigure
      (maybe now you have to quit LyX & restart? I don't remember, but I think it's unlikely)
4. However, when you do that and then try to export a file to "OpenOffice.org Writer" format you get lots of errors that say things like this:
--- warning --- Can't find/open file `tex4ht.env | .tex4ht'
It turns out that the file is at /etc/tex4ht/tex4ht.env. However, I think the package must be configured incorrectly so it doesn't find the file properly.
5. I have found one way to get oolatex to run from the command line, by doing this:
tex4ht oolatex -e/etc/tex4ht/tex4ht.env <latex_file_to_convert>
However, it doesn't seem to output a final .sxw or .odt file; it also seems to generate a .dvi that is 29 pages long even on a 2-line latex file!

So it seems to me that something is really weird and broken about how all this works in (K)ubuntu. I've heard on the LyX mailing list that all this "just works" on Fedora, so I don't think it's just that none of this software does what is advertised...

Has anyone else had any experience with this? Thanks in advance!

---

### Post by hogweed on 2007-05-31
I haven't been able to get the direct export from LyX either, but I have found a bit of a workaround. Currently I am preparing a book manuscript in LyX that the publisher nonetheless needs in .doc format (with each chapter as a separate document).

Here is the process that I go through for each file:

> First: do all work on a single file in a separate /test directory at /home/user/Desktop. (For some reason either this does not work on a fat32 partition, or else file location might be too long if done in an odd directory.)

Regular file:
Step 1: export from LyX to .tex with formatting as basic as possible (you will be reformatting some of the text anyway once it is in OpenOffice)
Step 2: run command: latex filename.tex (several times)
Step 3: run command: tex4ht filename.tex
Step 4: run command: mk4ht oolatex filename.tex

among the many files sitting in your directory now should be filename.odt, which you can open with OpenOffice and convert to .doc if necessary.

File with bibliography:
Step 1: place both the LyX file and associated .bib file in your test directory.
Step 2: export from LyX to .tex with formatting as basic as possible
Step 3: run command: latex filename.tex (several times)
Step 4: run command: bibtex filename.aux (several times)
Step 5: (again) run command: latex filename.tex (several times)
Step 6: run command: tex4ht filename.tex
Step 7: run command: mk4ht oolatex filename.tex

among the many files sitting in your directory now should be filename.odt, which you can open with OpenOffice and convert to .doc if necessary.

Anyway, this is what I have been doing -- hopefully the next version of LyX (1.5.0??) in Ubuntu will have all of this ironed out. In the meantime, I hope this works for you.

--hogweed

---

### Post by Typhoon on 2007-05-31
On my Debian Etch machine, running

/usr/share/tex4ht/oolatex <base name of tex file>

produces the required .odt file when run in the directory containing the tex file.

According to the man file, oolatex is just a script that invokes mk4ht with various options necessary to output the .odt file. In other words, mk4ht is the all-purpose command. The "shortcut" commands like htlatex and oolatex simply invoke mk4ht with the appropriate options.

On some files, I find that the process pauses with a message such as "typewriter fonts not supported" or some such. Simply hitting Enter starts it again. This may happen several times, but the end result is a .odt file that can then be loaded into OpenOffice.org.

HTH,
Typhoon

---

### Post by bossanova on 2007-06-05
I've finally worked it out. Here's how you export to OpenDocument in LyX 1.4.3:

Make sure tex4ht is installed:
apt get install tex4ht ... or use synaptic

Open tools-->preferences-->file formats

Create a new format: odt
GUI name: OpenDocument
Shortcut: whatever
Extension: odt
Viewer: oowriter (although I can't yet get the viewer and editor to work)
Editor: oowriter

Now go to tools-->preferences-->converters

create a new converter from LaTeX (plain) to OpenDocument
Converter: mk4ht oolatex $$i
Extra flag: originaldir,needaux

Now do File-->Export-->OpenDocument. Ignore the error message. Open your new OpenDocument document in OpenOffice.

---

### Post by timmie on 2007-07-30
Hello,
I have a newly installed Lyx 1.5.0.

The converter as described in
[http://bugzilla.lyx.org/show_bug.cgi?id=2085#c5](http://bugzilla.lyx.org/show_bug.cgi?id=2085#c5)
doesn't show any result here.

Can anyone confirm this?
I am ready to file a bug report on this!

There's another:
tex4ht doesn't work proper
[https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/90741](https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/90741)

---

### Post by timmie on 2007-07-30
I entered a bug report:

latex is not in PATH and conversion not working
[https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/129246](https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/129246)

---

### Post by timmie on 2007-08-08
I configured and installed Lyx 1.5.1 with checkinstall.

Now it works. My document was exported as ODF and I could open it in OOo!

[http://bugzilla.lyx.org/show_bug.cgi?id=2085#c12](http://bugzilla.lyx.org/show_bug.cgi?id=2085#c12)
[https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/129246](https://bugs.launchpad.net/ubuntu/+source/tex4ht/+bug/129246)

---

