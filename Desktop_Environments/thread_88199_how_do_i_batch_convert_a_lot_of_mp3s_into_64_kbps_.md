---
title: "how do i batch convert a lot of mp3s into 64 kbps MONO ?"
date: 2005-11-09
forum: Desktop Environments
---

### Post by jamesford on 2005-11-09
hi ive tried a lot of audio programs, like audacity and sound converter plus the audio convert nautilus script. the problem is that none of them can do both batch conversion AND convert to 64 kbps mono...which really is what i need. any clues what i can do ? is there like a command i can run like for example: convert --64kbps --mono /dir/manyfiles/*.mp3 or something like that ?

---

### Post by Dr. Nick on 2005-11-09
Install sound converter, It does batch and can go to 64bit, not sure if its mono or not, I beleive it would be the same as the souurce file

---

### Post by jamesford on 2005-11-09
ive got sound converter, but it doesent do mono

---

### Post by Dr. Nick on 2005-11-09
oops, didnt realize you had tried sound converter, I see it in you origional post now though. I dont know how to make it mono, or if its easily possible

---

### Post by Dr. Nick on 2005-11-09
Just saw this page
[http://sox.sourceforge.net/](http://sox.sourceforge.net/)

its mentioned [here]("http://lists.suse.com/archive/suse-linux-e/2004-Jul/2131.html")  that you can use a -c flag to change channels. Never used this program but see that it is avaible in synaptic, may need universe , not sure.

Also dont know if it can do a batch. The only other idea I have is to burn them to a cd and then re-rip in mono, but would be a waste of a CD


This newsgroup post shows what flags to use to convert but doenst mention how to do batch [http://groups.google.com/group/comp.sys.mac.apps/browse_thread/thread/ba64b8f271e7a8f5/4d0dc3f6e2e90c08?lnk=st&q=sox+batch+convert&rnum=4#4d0dc3f6e2e90c08](http://groups.google.com/group/comp.sys.mac.apps/browse_thread/thread/ba64b8f271e7a8f5/4d0dc3f6e2e90c08?lnk=st&q=sox+batch+convert&rnum=4#4d0dc3f6e2e90c08)

I have heard batch is possible though , but havent used sox myself

---

### Post by metasyntax on 2005-11-09
install lame, the use that to convert:

```

$> lame -a -b 64 input.mp3 64mono-output.mp3

```

or to do that for all mp3's in a directory:

```

$> for x in [ `ls -1 *.mp3` ]; do lame -a -b 64 $x mono64-${x}; done

```

This will convert all mp3's in a directory to 64kb, mono, and prefix the new file with "mono64".

HTH,
meta

---

### Post by HermanAB on 2005-11-09
Here isa guide that may help:
[http://www.aerospacesoftware.com/ogg2mp3-howto.html](http://www.aerospacesoftware.com/ogg2mp3-howto.html)

---

### Post by jamesford on 2005-11-10
thank you everyone! ill try it all out :)

---

### Post by sensimilla on 2008-05-25
I found that the command in post #6 does not like spaces in the filenames so I modified it slightly to work in more cases.

```
for x in *.mp3 ; do lame -a -b 64 "$x" mono64-"${x}"; done
```

note that this just does a simple conversion and will not copy the id3 tags to the new file.

---

### Post by teledyn on 2008-06-11
> **sensimilla said:**
> note that this just does a simple conversion and will not copy the id3 tags to the new file.

and so it does, which prompts the next question: *can we convert a batch of mp3s while _preserving_ the id3 tags?:(*

---

