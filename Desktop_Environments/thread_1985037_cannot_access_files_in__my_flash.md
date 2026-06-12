---
title: "cannot access files in  my flash"
date: 2012-05-22
forum: Desktop Environments
---

### Post by forsubhi on 2012-05-22
when I plug my flash , I cannot access the file in it with dolphin and when I write ls command in konsol , this output appear 

```
subhi@subhi-pc:/media/1616-447A$ ls
ls: cannot access CoMQWT&#963;r.a á: Input/output error
ls: cannot access ou cn3.ñ#: Input/output error
ls: cannot access rEc&#920;&#9567;LE&#9561;. ">: Input/output error
ls: cannot access ]n____~1. `!: Input/output error
ls: cannot access RTEOC n.&#9557;b: Input/output error
ls: cannot access &#963;f: Input/output error
ls: cannot access RPNK&#934;Gn1. 2: Input/output error
ls: cannot access US^íO:~=: Input/output error
ls: cannot access C<D(./: No such file or directory
ls: cannot access S&#9532;S[IM>1.0&: Input/output error
ls: cannot access DoUFL ".ç !: Input/output error
ls: cannot access JO&#9562;D@ .`!: Input/output error
ls: cannot access tL(@e&#949;.1: Input/output error
ls: cannot access FK17~±!.0]: Input/output error
ls: cannot access RrInT tÇ.! r: Input/output error
ls: cannot access fETNAUE.` b: Input/output error
ls: cannot access _E@HH/^."(p: No such file or directory
ls: cannot access SH!HEV3.ç01: Input/output error
(2) Facebook.mht
aaaa.txt
Adapting.fxml
Adapting.rar
add.txt
A?DIAK??.?Hw
All1.txt
amjad wav.rar
&#9604;AN&#9572;u@v&#9571;.DYT
aptjas.ZKP
Arabic.dic
ArabicOrdered.txt
Arabic.rar
Arabic_test.transcription
args for bw windows.txt
av@ficp.t?f
BaVH&#9573;t^?.Z?X
&#9579;&#9555;BH]-ní.AU?
bin
C<D(.?/?

```

my flash file system is ntfs
how can I solve this problem ?

---

### Post by erind on 2012-05-22
Just recently I had the same issue as yours. That shows a file system error or a USB hardware failure.
First back up your data if possible. Then try a disk-check from Windows (chkdsk), *fsck.ntfs *in Linux, or other check tools. Try them a few times. If not successful reformat the USB drive.
And if that does not work (which was my case) then your USB has a hardware failure - it's time for a replacement.

---

### Post by forsubhi on 2012-05-22
thank you erind , I 'll try that

---

