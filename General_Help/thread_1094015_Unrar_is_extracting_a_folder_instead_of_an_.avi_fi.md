---
title: "Unrar is extracting a folder instead of an .avi file"
date: 2009-03-12
forum: General Help
---

### Post by VotaVader on 2009-03-12
I'm trying to unpack some TV episodes that come in multiple rar files. When I try to extract the .avi file, I instead get a folder with the name of the episode (.avi extension included). I've tried using the "Extract Here" on the .rar file (not the numbered ones), and also multiple times through the terminal, but I keep getting the same result.

Again, the file name is correct (like Example.S01E15.hdtv.XviD-blah.avi), but it's not a movie file, it's a folder with nothing in it...
Any suggestions?
Thanks

---

### Post by binbash on 2009-03-12
please unrar it at terminal (unrar e filename.r00 or filename.part1.rar etc etc)

---

### Post by VotaVader on 2009-03-12
> **binbash said:**
> please unrar it at terminal (unrar e filename.r00 or filename.part1.rar etc etc)

Here's what I get when unraring at terminal.
```

pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ unrar house.s05e12.hdtv.xvid-fqm.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/pedro/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.rar

All OK

```

I've also tried it with one of the part files (i.e. .r00) and adding the -x or x options to the unrar. Always with the same effect. Keep getting a folder instead of an avi file.

---

### Post by binbash on 2009-03-12
Dude please go to the directory which contains rar files and paste the output of ls at that directory (sample : cd /home/user/videos then ls )

---

### Post by VotaVader on 2009-03-13
> **binbash said:**
> Dude please go to the directory which contains rar files and paste the output of ls at that directory (sample : cd /home/user/videos then ls )

Here goes:
```
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ ls
house.s05e12.hdtv.xvid-fqm.avi  house.s05e12.hdtv.xvid-fqm.r10
house.s05e12.hdtv.xvid-fqm.nfo  house.s05e12.hdtv.xvid-fqm.r11
house.s05e12.hdtv.xvid-fqm.r00  house.s05e12.hdtv.xvid-fqm.r12
house.s05e12.hdtv.xvid-fqm.r01  house.s05e12.hdtv.xvid-fqm.r13
house.s05e12.hdtv.xvid-fqm.r02  house.s05e12.hdtv.xvid-fqm.r14
house.s05e12.hdtv.xvid-fqm.r03  house.s05e12.hdtv.xvid-fqm.r15
house.s05e12.hdtv.xvid-fqm.r04  house.s05e12.hdtv.xvid-fqm.r16
house.s05e12.hdtv.xvid-fqm.r05  house.s05e12.hdtv.xvid-fqm.r17
house.s05e12.hdtv.xvid-fqm.r06  house.s05e12.hdtv.xvid-fqm.rar
house.s05e12.hdtv.xvid-fqm.r07  house.s05e12.hdtv.xvid-fqm.sfv
house.s05e12.hdtv.xvid-fqm.r08  Sample
house.s05e12.hdtv.xvid-fqm.r09
```

This is after unraring, of course. The .avi file that you see there is actually a folder and is highlighted in light blue on the terminal.

---

### Post by binbash on 2009-03-13
rm the avi.Then 

unrar e house.s05e12.hdtv.xvid-fqm.r00

This should extract the video.If there is still .avi folder then nagivate into it and check if the video is there or not

---

### Post by VotaVader on 2009-03-13
> **binbash said:**
> rm the avi.Then 

unrar e house.s05e12.hdtv.xvid-fqm.r00

This should extract the video.If there is still .avi folder then nagivate into it and check if the video is there or not

Ok, done. It still outputs a folder and there's nothing in it. Here are the steps I took in the terminal:

```
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ ls
house.s05e12.hdtv.xvid-fqm.nfo  house.s05e12.hdtv.xvid-fqm.r10
house.s05e12.hdtv.xvid-fqm.r00  house.s05e12.hdtv.xvid-fqm.r11
house.s05e12.hdtv.xvid-fqm.r01  house.s05e12.hdtv.xvid-fqm.r12
house.s05e12.hdtv.xvid-fqm.r02  house.s05e12.hdtv.xvid-fqm.r13
house.s05e12.hdtv.xvid-fqm.r03  house.s05e12.hdtv.xvid-fqm.r14
house.s05e12.hdtv.xvid-fqm.r04  house.s05e12.hdtv.xvid-fqm.r15
house.s05e12.hdtv.xvid-fqm.r05  house.s05e12.hdtv.xvid-fqm.r16
house.s05e12.hdtv.xvid-fqm.r06  house.s05e12.hdtv.xvid-fqm.r17
house.s05e12.hdtv.xvid-fqm.r07  house.s05e12.hdtv.xvid-fqm.rar
house.s05e12.hdtv.xvid-fqm.r08  house.s05e12.hdtv.xvid-fqm.sfv
house.s05e12.hdtv.xvid-fqm.r09  Sample
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ unrar house.s05e12.hdtv.xvid-fqm.r00

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/pedro/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.r00

All OK
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ ls
house.s05e12.hdtv.xvid-fqm.avi  house.s05e12.hdtv.xvid-fqm.r10
house.s05e12.hdtv.xvid-fqm.nfo  house.s05e12.hdtv.xvid-fqm.r11
house.s05e12.hdtv.xvid-fqm.r00  house.s05e12.hdtv.xvid-fqm.r12
house.s05e12.hdtv.xvid-fqm.r01  house.s05e12.hdtv.xvid-fqm.r13
house.s05e12.hdtv.xvid-fqm.r02  house.s05e12.hdtv.xvid-fqm.r14
house.s05e12.hdtv.xvid-fqm.r03  house.s05e12.hdtv.xvid-fqm.r15
house.s05e12.hdtv.xvid-fqm.r04  house.s05e12.hdtv.xvid-fqm.r16
house.s05e12.hdtv.xvid-fqm.r05  house.s05e12.hdtv.xvid-fqm.r17
house.s05e12.hdtv.xvid-fqm.r06  house.s05e12.hdtv.xvid-fqm.rar
house.s05e12.hdtv.xvid-fqm.r07  house.s05e12.hdtv.xvid-fqm.sfv
house.s05e12.hdtv.xvid-fqm.r08  Sample
house.s05e12.hdtv.xvid-fqm.r09
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ cd house.s05e12.hdtv.xvid-fqm.avi
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.avi$ ls
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.avi$ 
```

---

### Post by lloyd_b on 2009-03-13
Try deleting that ".avi" directory again, and then:
```
unrar **e** house.s05e12.hdtv.xvid-fqm.rar
```
I'm not sure what effect of running unrar without the "e" (extract to current directory) option is - this may be the root of your problem.

Lloyd B.

---

### Post by VotaVader on 2009-03-13
> **lloyd_b said:**
> Try deleting that ".avi" directory again, and then:
```
unrar **e** house.s05e12.hdtv.xvid-fqm.rar
```
I'm not sure what effect of running unrar without the "e" (extract to current directory) option is - this may be the root of your problem.

Lloyd B.

Ok, tried that and nothing happened (not even the .avi directory appeared). The unrar seemed to work fine, but the file didn't extract.
```

pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ ls
house.s05e12.hdtv.xvid-fqm.nfo  house.s05e12.hdtv.xvid-fqm.r10
house.s05e12.hdtv.xvid-fqm.r00  house.s05e12.hdtv.xvid-fqm.r11
house.s05e12.hdtv.xvid-fqm.r01  house.s05e12.hdtv.xvid-fqm.r12
house.s05e12.hdtv.xvid-fqm.r02  house.s05e12.hdtv.xvid-fqm.r13
house.s05e12.hdtv.xvid-fqm.r03  house.s05e12.hdtv.xvid-fqm.r14
house.s05e12.hdtv.xvid-fqm.r04  house.s05e12.hdtv.xvid-fqm.r15
house.s05e12.hdtv.xvid-fqm.r05  house.s05e12.hdtv.xvid-fqm.r16
house.s05e12.hdtv.xvid-fqm.r06  house.s05e12.hdtv.xvid-fqm.r17
house.s05e12.hdtv.xvid-fqm.r07  house.s05e12.hdtv.xvid-fqm.rar
house.s05e12.hdtv.xvid-fqm.r08  house.s05e12.hdtv.xvid-fqm.sfv
house.s05e12.hdtv.xvid-fqm.r09  Sample
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ unrar e house.s05e12.hdtv.xvid-fqm.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/pedro/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.rar

All OK
pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ ls
house.s05e12.hdtv.xvid-fqm.nfo  house.s05e12.hdtv.xvid-fqm.r10
house.s05e12.hdtv.xvid-fqm.r00  house.s05e12.hdtv.xvid-fqm.r11
house.s05e12.hdtv.xvid-fqm.r01  house.s05e12.hdtv.xvid-fqm.r12
house.s05e12.hdtv.xvid-fqm.r02  house.s05e12.hdtv.xvid-fqm.r13
house.s05e12.hdtv.xvid-fqm.r03  house.s05e12.hdtv.xvid-fqm.r14
house.s05e12.hdtv.xvid-fqm.r04  house.s05e12.hdtv.xvid-fqm.r15
house.s05e12.hdtv.xvid-fqm.r05  house.s05e12.hdtv.xvid-fqm.r16
house.s05e12.hdtv.xvid-fqm.r06  house.s05e12.hdtv.xvid-fqm.r17
house.s05e12.hdtv.xvid-fqm.r07  house.s05e12.hdtv.xvid-fqm.rar
house.s05e12.hdtv.xvid-fqm.r08  house.s05e12.hdtv.xvid-fqm.sfv
house.s05e12.hdtv.xvid-fqm.r09  Sample
```

Also tried the same with the .r00 file. Same results. This is really weird.

---

### Post by lloyd_b on 2009-03-13
You may just be looking at a corrupt archive...

Try:
```
unrar l house.s05e12.hdtv.xvid-fqm.rar
```to see exactly what files are contained in the archive.

Lloyd B.

---

### Post by VotaVader on 2009-03-14
> **lloyd_b said:**
> You may just be looking at a corrupt archive...

Try:
```
unrar l house.s05e12.hdtv.xvid-fqm.rar
```to see exactly what files are contained in the archive.

Lloyd B.

Yeah. I was kinda coming to that conclusion too... it's just that it happened with more than one archive and I don't have any old ones to try out (that have worked before). I guess I'll try downloading again and seeing if the problem persists.
Anyway, here's the output for unrar l:
```

pedro@pedro-laptop:~/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM$ unrar l house.s05e12.hdtv.xvid-fqm.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


RAR archive /home/pedro/utorrent/Downloads/House.S05E12.Painless.HDTV.XviD-FQM/house.s05e12.hdtv.xvid-fqm.rar

Pathname/Comment
                  Size   Packed Ratio  Date   Time     Attr      CRC   Meth Ver
-------------------------------------------------------------------------------
 house.s05e12.hdtv.xvid-fqm.avi
             366978484 19999896   5% 19-01-09 22:21   .D....   14342954 m0? 2.0
-------------------------------------------------------------------------------
    1        366978484 19999896   5%
```

---

### Post by kroiz on 2010-05-28
I am having similar problem.
how can I tell if the file is corrupted? has anyone been successful with extracting a split rar?

---

### Post by VotaVader on 2010-05-28
> **kroiz said:**
> I am having similar problem.
how can I tell if the file is corrupted? has anyone been successful with extracting a split rar?

I had that problem a reaaally long time ago, so I'm not sure how I solved it, but I believe it *was* a corrupt file problem. I had to download again in the end (although I'm not certain if I downloaded the same one).

I was living in Australia at the time so every MB of internet traffic was precious, hehe, I guess that's why I went to all the trouble without trying a fresh download...

Hope you solve your problem.

---

### Post by kroiz on 2010-06-01
I downloaded the file again in a non rar version...

---

