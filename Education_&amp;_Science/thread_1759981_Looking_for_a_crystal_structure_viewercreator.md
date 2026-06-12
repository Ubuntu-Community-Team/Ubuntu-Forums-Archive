---
title: "Looking for a crystal structure viewer/creator"
date: 2011-05-16
forum: Education &amp; Science
---

### Post by KIAaze on 2011-05-16
Hi,

I'm looking for a crystal structure viewer/creator.
Ideally something easy to use and which comes with some standard examples like CC and FCC structures.

I installed a few related packages through synaptics like gnome crystal and avogadro, but am still trying to figure out how to even create a crystal in them.

At the moment, I really just want to create some nice pictures of an FCC structure from different directions.

Any suggestions?

---

### Post by Lateralis on 2011-05-16
I have used three different crystal viewers in my time.  RasMol was a good one to get going with.  Not used it for a while, but does make shiny images. 

XCrysDen is what I have used most often.  It again makes pretty pictures.  I'm not sure you can actually "build" crystal with it - at least, I haven't - but you can give it a list of atoms in an xyz-type format and it will happily display it. 

The third and most powerful program is VESTA.  It is free and open source (like the others) but has a built in crystal builder, you can orient your crystal in any way you like, add crystal planes, export as .eps etc...  To build a crystal you can either give it a an xyz-list as with the other two, or, if you know the space group (for instance, F-43m for zinc blende) then you can build a crystal fairly quickly.

---

### Post by gabrielaca on 2011-06-19
hi Lateralis i tried to find VESTA on the repos but wasnt there, is on other repo? i tried googleing it but did not find anything; could you point me to where to find it? thanks.

---

### Post by Lateralis on 2011-06-20
Sure no worries: [Vesta]("http://www.geocities.jp/kmo_mma/crystal/en/vesta.html").

The download link contains 32- and 64-bit tarballs that you can download.  I believe there is a binary executable that you can simply run, once you have extracted the file. You can move the binary to whichever directory you like, such as /usr/local/bin, ~/bin or somewhere else that might be in your $PATH.

---

