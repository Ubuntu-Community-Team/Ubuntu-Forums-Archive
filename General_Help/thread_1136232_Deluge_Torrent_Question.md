---
title: "Deluge Torrent Question"
date: 2009-04-24
forum: General Help
---

### Post by qjmoss on 2009-04-24
Okay, this is probably a silly question. I just started using the Deluge torrent client, in replace for my Transmission app. 

Now, when I start some torrents, get up and walk away, some of my torrents have an error.

This is starting to cause my some frustration, on account of my trackers ratio.

I don't really know what the problem could be, maybe it's the tracker, missing files? maybe it's because there is an issue with my external hard drive that I'm saving my files too?

I'm really not sure, and I know I haven't given enough information on my issue, but if anyone has some ideas on where to start it would be greatly appreciated!

Thank you for your time!


-Quentin

---

### Post by Rocket2DMn on 2009-04-24
Can you tell us what the error says or post a screenshot please?

---

### Post by evermooingcow on 2009-04-24
Sorry if this is a dumb question but did you give write access to the download path?

---

### Post by qjmoss on 2009-04-24
I really just havent looked into this client, I don't even know where to get error out puts.. maybe i'm missing something in front of me, but this is what i see.

Hope it helps

---

### Post by Rocket2DMn on 2009-04-24
Can you please click on the Error section on the left side.  Please don't post screenshots showing us what you are downloading - ignorance is bliss.  We just want to know the error.

---

### Post by qjmoss on 2009-04-25
The errors i am getting are

No such file or directory

and 

Permission denied 

=/


It's a little upsetting

---

### Post by qjmoss on 2009-04-25
I've noticed that sometimes my external will unmount.

Could this be the problem?

and is there any reason it would do that?

---

### Post by kpkeerthi on 2009-04-25
> **qjmoss said:**
> I've noticed that sometimes my external will unmount.

Could this be the problem?

Yes.

> 
and is there any reason it would do that?
Not sure why it happens to you.

---

### Post by Rocket2DMn on 2009-04-25
It sounds when it says no such file or directory, then your external is unmounted.  When it says permission denied, it means that you don't have write access to the drive.

What version of Ubuntu are you using and what is your external USB drive make/model?  Some drives have power saving features which can result in the device unmounting itself automatically, esp. in older versions of Ubuntu.

---

### Post by qjmoss on 2009-04-25
Hm.. ok.

---

### Post by qjmoss on 2009-04-25
I'm running Ubuntu 8.10

My external is western digital Model-10EAVS

---

### Post by qjmoss on 2009-04-25
Add a 


"Input/output error"

on top of it

---

### Post by Rocket2DMn on 2009-04-25
Are you able to manually add files/folders to the directory on the external when it is mounted?  That is to say, can you open the directory in nautilus and create or copy files to there?

Can you please post the output of
```
dmesg
```
(wrap it in [noparse]```

```[/noparse] tags please)

---

### Post by qjmoss on 2009-04-25
Yes I can open the external just like any other directory. such as Home, Documents.

add new folders copy and paste.


It's just strange, because i've been running it the same way for awhile, and one day.. bam, all my torrents had errors.

---

### Post by qjmoss on 2009-04-25
```
[35798.906779] FAT: FAT read failed (blocknr 84779)
[35798.906794] FAT: FAT read failed (blocknr 84779)
[35798.906808] FAT: FAT read failed (blocknr 84779)
[35798.906823] FAT: FAT read failed (blocknr 84779)
[35798.906837] FAT: FAT read failed (blocknr 84779)
[35798.906855] FAT: FAT read failed (blocknr 84779)
[35798.906873] FAT: FAT read failed (blocknr 84779)
[35798.906890] FAT: FAT read failed (blocknr 84779)
[35798.906904] FAT: FAT read failed (blocknr 84779)
[35798.906919] FAT: FAT read failed (blocknr 84779)
[35798.906933] FAT: FAT read failed (blocknr 84779)
[35798.906947] FAT: FAT read failed (blocknr 84779)
[35798.906962] FAT: FAT read failed (blocknr 84779)
[35798.906976] FAT: FAT read failed (blocknr 84779)
[35798.906994] FAT: FAT read failed (blocknr 84779)
[35798.907011] FAT: FAT read failed (blocknr 84779)
[35798.907026] FAT: FAT read failed (blocknr 84779)
[35798.907041] FAT: FAT read failed (blocknr 84779)
[35798.907055] FAT: FAT read failed (blocknr 84779)
[35798.907069] FAT: FAT read failed (blocknr 84779)
[35798.907084] FAT: FAT read failed (blocknr 84779)
[35798.907098] FAT: FAT read failed (blocknr 84779)
[35798.907112] FAT: FAT read failed (blocknr 84779)
[35798.907130] FAT: FAT read failed (blocknr 84779)
[35798.907146] FAT: FAT read failed (blocknr 84779)
[35798.907161] FAT: FAT read failed (blocknr 84779)
[35798.907176] FAT: FAT read failed (blocknr 84779)
[35798.907190] FAT: FAT read failed (blocknr 84779)
[35798.907204] FAT: FAT read failed (blocknr 84779)
[35798.907219] FAT: FAT read failed (blocknr 84779)
[35798.907233] FAT: FAT read failed (blocknr 84779)
[35798.907247] FAT: FAT read failed (blocknr 84779)
[35798.907264] FAT: FAT read failed (blocknr 84779)
[35798.907281] FAT: FAT read failed (blocknr 84779)
[35798.907297] FAT: FAT read failed (blocknr 84779)
[35798.907311] FAT: FAT read failed (blocknr 84779)
[35798.907326] FAT: FAT read failed (blocknr 84779)
[35798.907340] FAT: FAT read failed (blocknr 84779)
[35798.907355] FAT: FAT read failed (blocknr 84779)
[35798.907369] FAT: FAT read failed (blocknr 84779)
[35798.907383] FAT: FAT read failed (blocknr 84779)
[35798.907401] FAT: FAT read failed (blocknr 84779)
[35798.907417] FAT: FAT read failed (blocknr 84779)
[35798.907432] FAT: FAT read failed (blocknr 84779)
[35798.907447] FAT: FAT read failed (blocknr 84779)
[35798.907461] FAT: FAT read failed (blocknr 84779)
[35798.907475] FAT: FAT read failed (blocknr 84779)
[35798.907490] FAT: FAT read failed (blocknr 84779)
[35798.907504] FAT: FAT read failed (blocknr 84779)
[35798.907519] FAT: FAT read failed (blocknr 84779)
[35798.907536] FAT: FAT read failed (blocknr 84779)
[35798.907552] FAT: FAT read failed (blocknr 84779)
[35798.907567] FAT: FAT read failed (blocknr 84779)
[35798.907582] FAT: FAT read failed (blocknr 84779)
[35798.907597] FAT: FAT read failed (blocknr 84779)
[35798.907611] FAT: FAT read failed (blocknr 84779)
[35798.907626] FAT: FAT read failed (blocknr 84779)
[35798.907640] FAT: FAT read failed (blocknr 84779)
[35798.907655] FAT: FAT read failed (blocknr 84779)
[35798.907672] FAT: FAT read failed (blocknr 84779)
[35798.907689] FAT: FAT read failed (blocknr 84779)
[35798.907704] FAT: FAT read failed (blocknr 84779)
[35798.907719] FAT: FAT read failed (blocknr 84779)
[35798.907734] FAT: FAT read failed (blocknr 84779)
[35798.907748] FAT: FAT read failed (blocknr 84779)
[35798.907763] FAT: FAT read failed (blocknr 84779)
[35798.907777] FAT: FAT read failed (blocknr 84779)
[35798.907792] FAT: FAT read failed (blocknr 84779)
[35798.907812] FAT: FAT read failed (blocknr 84779)
[35798.907830] FAT: FAT read failed (blocknr 84779)
[35798.907845] FAT: FAT read failed (blocknr 84779)
[35798.907860] FAT: FAT read failed (blocknr 84779)
[35798.907874] FAT: FAT read failed (blocknr 84779)
[35798.907889] FAT: FAT read failed (blocknr 84779)
[35798.907903] FAT: FAT read failed (blocknr 84779)
[35798.907917] FAT: FAT read failed (blocknr 84779)
[35798.907932] FAT: FAT read failed (blocknr 84779)
[35798.907950] FAT: FAT read failed (blocknr 84779)
[35798.907968] FAT: FAT read failed (blocknr 84779)
[35798.907984] FAT: FAT read failed (blocknr 84779)
[35798.907999] FAT: FAT read failed (blocknr 84779)
[35798.908014] FAT: FAT read failed (blocknr 84779)
[35798.908028] FAT: FAT read failed (blocknr 84779)
[35798.908043] FAT: FAT read failed (blocknr 84779)
[35798.908057] FAT: FAT read failed (blocknr 84779)
[35798.908071] FAT: FAT read failed (blocknr 84779)
[35798.908089] FAT: FAT read failed (blocknr 84779)
[35798.908106] FAT: FAT read failed (blocknr 84779)
[35798.908120] FAT: FAT read failed (blocknr 84779)
[35798.908135] FAT: FAT read failed (blocknr 84779)
[35798.908149] FAT: FAT read failed (blocknr 84779)
[35798.908164] FAT: FAT read failed (blocknr 84779)
[35798.908178] FAT: FAT read failed (blocknr 84779)
[35798.908192] FAT: FAT read failed (blocknr 84779)
[35798.908207] FAT: FAT read failed (blocknr 84779)
[35798.908224] FAT: FAT read failed (blocknr 84779)
[35798.908240] FAT: FAT read failed (blocknr 84779)
[35798.908255] FAT: FAT read failed (blocknr 84779)
[35798.908269] FAT: FAT read failed (blocknr 84779)
[35798.908284] FAT: FAT read failed (blocknr 84779)
[35798.908298] FAT: FAT read failed (blocknr 84779)
[35798.908313] FAT: FAT read failed (blocknr 84779)
[35798.908327] FAT: FAT read failed (blocknr 84779)
[35798.908342] FAT: FAT read failed (blocknr 84779)
[35798.908359] FAT: FAT read failed (blocknr 84779)
[35798.908376] FAT: FAT read failed (blocknr 84779)
[35798.908391] FAT: FAT read failed (blocknr 84779)
[35798.908406] FAT: FAT read failed (blocknr 84779)
[35798.908420] FAT: FAT read failed (blocknr 84779)
[35798.908435] FAT: FAT read failed (blocknr 84779)
[35798.908449] FAT: FAT read failed (blocknr 84779)
[35798.908464] FAT: FAT read failed (blocknr 84779)
[35798.908478] FAT: FAT read failed (blocknr 84779)
[35798.908496] FAT: FAT read failed (blocknr 84779)
[35798.908514] FAT: FAT read failed (blocknr 84779)
[35798.908528] FAT: FAT read failed (blocknr 84779)
[35798.908543] FAT: FAT read failed (blocknr 84779)
[35798.908559] FAT: FAT read failed (blocknr 84779)
[35798.908574] FAT: FAT read failed (blocknr 84779)
[35798.908589] FAT: FAT read failed (blocknr 84779)
[35798.908604] FAT: FAT read failed (blocknr 84779)
[35798.908619] FAT: FAT read failed (blocknr 84779)
[35798.908698] FAT: FAT read failed (blocknr 84779)
[35798.908717] FAT: FAT read failed (blocknr 84779)
[35798.908733] FAT: FAT read failed (blocknr 84779)
[35798.908747] FAT: FAT read failed (blocknr 84779)
[35798.908762] FAT: FAT read failed (blocknr 84779)
[35798.908776] FAT: FAT read failed (blocknr 84779)
[35798.908791] FAT: FAT read failed (blocknr 84779)
[35798.908805] FAT: FAT read failed (blocknr 84779)
[35798.908819] FAT: FAT read failed (blocknr 84779)
[35798.908837] FAT: FAT read failed (blocknr 84779)
[35798.908854] FAT: FAT read failed (blocknr 84779)
[35798.908869] FAT: FAT read failed (blocknr 84779)
[35798.908883] FAT: FAT read failed (blocknr 84779)
[35798.908898] FAT: FAT read failed (blocknr 84779)
[35798.908912] FAT: FAT read failed (blocknr 84779)
[35798.908927] FAT: FAT read failed (blocknr 84779)
[35798.908941] FAT: FAT read failed (blocknr 84779)
[35798.908955] FAT: FAT read failed (blocknr 84779)
[35798.908973] FAT: FAT read failed (blocknr 84779)
[35798.908991] FAT: FAT read failed (blocknr 84779)
[35798.909036] FAT: FAT read failed (blocknr 84779)
[35798.909051] FAT: FAT read failed (blocknr 84779)
[35798.909065] FAT: FAT read failed (blocknr 84779)
[35798.909080] FAT: FAT read failed (blocknr 84779)
[35798.909094] FAT: FAT read failed (blocknr 84779)
[35798.909108] FAT: FAT read failed (blocknr 84779)
[35798.909123] FAT: FAT read failed (blocknr 84779)
[35798.909141] FAT: FAT read failed (blocknr 84779)
[35798.909157] FAT: FAT read failed (blocknr 84779)
[35798.909172] FAT: FAT read failed (blocknr 84779)
[35798.909186] FAT: FAT read failed (blocknr 84779)
[35798.909201] FAT: FAT read failed (blocknr 84779)
[35798.909215] FAT: FAT read failed (blocknr 84779)
[35798.909229] FAT: FAT read failed (blocknr 84779)
[35798.909244] FAT: FAT read failed (blocknr 84779)
[35798.909258] FAT: FAT read failed (blocknr 84779)
[35798.909275] FAT: FAT read failed (blocknr 84779)
[35798.909292] FAT: FAT read failed (blocknr 84779)
[35798.909306] FAT: FAT read failed (blocknr 84779)
[35798.909321] FAT: FAT read failed (blocknr 84779)
[35798.909335] FAT: FAT read failed (blocknr 84779)
[35798.909350] FAT: FAT read failed (blocknr 84779)
[35798.909364] FAT: FAT read failed (blocknr 84779)
[35798.909379] FAT: FAT read failed (blocknr 84779)
[35798.909393] FAT: FAT read failed (blocknr 84779)
[35798.909410] FAT: FAT read failed (blocknr 84779)
[35798.909426] FAT: FAT read failed (blocknr 84779)
[35798.909441] FAT: FAT read failed (blocknr 84779)
[35798.909456] FAT: FAT read failed (blocknr 84779)
[35798.909470] FAT: FAT read failed (blocknr 84779)
[35798.909485] FAT: FAT read failed (blocknr 84779)
[35798.909501] FAT: FAT read failed (blocknr 84779)
[35798.909516] FAT: FAT read failed (blocknr 84779)
[35798.909530] FAT: FAT read failed (blocknr 84779)
[35798.909549] FAT: FAT read failed (blocknr 84779)
[35798.909567] FAT: FAT read failed (blocknr 84779)
[35798.909582] FAT: FAT read failed (blocknr 84779)
[35798.909596] FAT: FAT read failed (blocknr 84779)
[35798.909611] FAT: FAT read failed (blocknr 84779)
[35798.909626] FAT: FAT read failed (blocknr 84779)
[35798.909640] FAT: FAT read failed (blocknr 84779)
[35798.909656] FAT: FAT read failed (blocknr 84779)
[35798.909671] FAT: FAT read failed (blocknr 84779)
[35798.909688] FAT: FAT read failed (blocknr 84779)
[35798.909706] FAT: FAT read failed (blocknr 84779)
[35798.909722] FAT: FAT read failed (blocknr 84779)
[35798.909736] FAT: FAT read failed (blocknr 84779)
[35798.909751] FAT: FAT read failed (blocknr 84779)
[35798.909765] FAT: FAT read failed (blocknr 84779)
[35798.909780] FAT: FAT read failed (blocknr 84779)
[35798.909794] FAT: FAT read failed (blocknr 84779)
[35798.909808] FAT: FAT read failed (blocknr 84779)
[35798.909829] FAT: FAT read failed (blocknr 84779)
[35798.909847] FAT: FAT read failed (blocknr 84779)
[35798.909863] FAT: FAT read failed (blocknr 84779)
[35798.909877] FAT: FAT read failed (blocknr 84779)
[35798.909891] FAT: FAT read failed (blocknr 84779)
[35798.909906] FAT: FAT read failed (blocknr 84779)
[35798.909920] FAT: FAT read failed (blocknr 84779)
[35798.909934] FAT: FAT read failed (blocknr 84779)
[35798.909949] FAT: FAT read failed (blocknr 84779)
[35798.909966] FAT: FAT read failed (blocknr 84779)
[35798.909983] FAT: FAT read failed (blocknr 84779)
[35798.909998] FAT: FAT read failed (blocknr 84779)
[35798.910012] FAT: FAT read failed (blocknr 84779)
[35798.910027] FAT: FAT read failed (blocknr 84779)
[35798.910041] FAT: FAT read failed (blocknr 84779)
[35798.910055] FAT: FAT read failed (blocknr 84779)
[35798.910070] FAT: FAT read failed (blocknr 84779)
[35798.910084] FAT: FAT read failed (blocknr 84779)
[35798.910101] FAT: FAT read failed (blocknr 84779)
[35798.910120] FAT: FAT read failed (blocknr 84779)
[35798.910135] FAT: FAT read failed (blocknr 84779)
[35798.910149] FAT: FAT read failed (blocknr 84779)
[35798.910163] FAT: FAT read failed (blocknr 84779)
[35798.910177] FAT: FAT read failed (blocknr 84779)
[35798.910192] FAT: FAT read failed (blocknr 84779)
[35798.910206] FAT: FAT read failed (blocknr 84779)
[35798.910221] FAT: FAT read failed (blocknr 84779)
[35798.910238] FAT: FAT read failed (blocknr 84779)
[35798.910255] FAT: FAT read failed (blocknr 84779)
[35798.910270] FAT: FAT read failed (blocknr 84779)
[35798.910284] FAT: FAT read failed (blocknr 84779)
[35798.910299] FAT: FAT read failed (blocknr 84779)
[35798.910313] FAT: FAT read failed (blocknr 84779)
[35798.910327] FAT: FAT read failed (blocknr 84779)
[35798.910342] FAT: FAT read failed (blocknr 84779)
[35798.910356] FAT: FAT read failed (blocknr 84779)
[35798.910373] FAT: FAT read failed (blocknr 84779)
[35798.910392] FAT: FAT read failed (blocknr 84779)
[35798.910408] FAT: FAT read failed (blocknr 84779)
[35798.910422] FAT: FAT read failed (blocknr 84779)
[35798.910437] FAT: FAT read failed (blocknr 84779)
[35798.910451] FAT: FAT read failed (blocknr 84779)
[35798.910466] FAT: FAT read failed (blocknr 84779)
[35798.910480] FAT: FAT read failed (blocknr 84779)
[35798.910494] FAT: FAT read failed (blocknr 84779)
[35798.910512] FAT: FAT read failed (blocknr 84779)
[35798.910530] FAT: FAT read failed (blocknr 84779)
[35798.910546] FAT: FAT read failed (blocknr 84779)
[35798.910560] FAT: FAT read failed (blocknr 84779)
[35798.910574] FAT: FAT read failed (blocknr 84779)
[35798.910589] FAT: FAT read failed (blocknr 84779)
[35798.910603] FAT: FAT read failed (blocknr 84779)
[35798.910617] FAT: FAT read failed (blocknr 84779)
[35798.910632] FAT: FAT read failed (blocknr 84779)
[35798.910649] FAT: FAT read failed (blocknr 84779)
[35798.910677] FAT: FAT read failed (blocknr 84779)
[35798.910692] FAT: FAT read failed (blocknr 84779)
[35798.910706] FAT: FAT read failed (blocknr 84779)
[35798.910721] FAT: FAT read failed (blocknr 84779)
[35798.910735] FAT: FAT read failed (blocknr 84779)
[35798.910750] FAT: FAT read failed (blocknr 84779)
[35798.910764] FAT: FAT read failed (blocknr 84779)
[35798.910778] FAT: FAT read failed (blocknr 84779)
[35798.910796] FAT: FAT read failed (blocknr 84779)
[35798.910812] FAT: FAT read failed (blocknr 84779)
[35798.910826] FAT: FAT read failed (blocknr 84779)
[35798.910841] FAT: FAT read failed (blocknr 84779)
[35798.910855] FAT: FAT read failed (blocknr 84779)
[35798.910870] FAT: FAT read failed (blocknr 84779)
[35798.910884] FAT: FAT read failed (blocknr 84779)
[35798.910898] FAT: FAT read failed (blocknr 84779)
[35798.910912] FAT: FAT read failed (blocknr 84779)
[35798.910930] FAT: FAT read failed (blocknr 84779)
[35798.910946] FAT: FAT read failed (blocknr 84779)
[35798.910960] FAT: FAT read failed (blocknr 84779)
[35798.910975] FAT: FAT read failed (blocknr 84779)
[35798.910989] FAT: FAT read failed (blocknr 84779)
[35798.911003] FAT: FAT read failed (blocknr 84779)
[35798.911018] FAT: FAT read failed (blocknr 84779)
[35798.911032] FAT: FAT read failed (blocknr 84779)
[35798.911046] FAT: FAT read failed (blocknr 84779)
[35798.911064] FAT: FAT read failed (blocknr 84779)
[35798.911080] FAT: FAT read failed (blocknr 84779)
[35798.911094] FAT: FAT read failed (blocknr 84779)
[35798.911108] FAT: FAT read failed (blocknr 84779)
[35798.911123] FAT: FAT read failed (blocknr 84779)
[35798.911171] FAT: FAT read failed (blocknr 84779)
[35798.911185] FAT: FAT read failed (blocknr 84779)
[35798.911200] FAT: FAT read failed (blocknr 84779)
[35798.911214] FAT: FAT read failed (blocknr 84779)
[35798.911232] FAT: FAT read failed (blocknr 84779)
[35798.911249] FAT: FAT read failed (blocknr 84779)
[35798.911265] FAT: FAT read failed (blocknr 84779)
[35798.911279] FAT: FAT read failed (blocknr 84779)
[35798.911294] FAT: FAT read failed (blocknr 84779)
[35798.911309] FAT: FAT read failed (blocknr 84779)
[35798.911324] FAT: FAT read failed (blocknr 84779)
[35798.911338] FAT: FAT read failed (blocknr 84779)
[35798.911353] FAT: FAT read failed (blocknr 84779)
[35798.911370] FAT: FAT read failed (blocknr 84779)
[35798.911387] FAT: FAT read failed (blocknr 84779)
[35798.911402] FAT: FAT read failed (blocknr 84779)
[35798.911417] FAT: FAT read failed (blocknr 84779)
[35798.911432] FAT: FAT read failed (blocknr 84779)
[35798.911447] FAT: FAT read failed (blocknr 84779)
[35798.911461] FAT: FAT read failed (blocknr 84779)
[35798.911476] FAT: FAT read failed (blocknr 84779)
[35798.911491] FAT: FAT read failed (blocknr 84779)
[35798.911508] FAT: FAT read failed (blocknr 84779)
[35798.911524] FAT: FAT read failed (blocknr 84779)
[35798.911539] FAT: FAT read failed (blocknr 84779)
[35798.911553] FAT: FAT read failed (blocknr 84779)
[35798.911568] FAT: FAT read failed (blocknr 84779)
[35798.911582] FAT: FAT read failed (blocknr 84779)
[35798.911597] FAT: FAT read failed (blocknr 84779)
[35798.911611] FAT: FAT read failed (blocknr 84779)
[35798.911626] FAT: FAT read failed (blocknr 84779)
[35798.911643] FAT: FAT read failed (blocknr 84779)
[35798.911659] FAT: FAT read failed (blocknr 84779)
[35798.911674] FAT: FAT read failed (blocknr 84779)
[35798.911688] FAT: FAT read failed (blocknr 84779)
[35798.911702] FAT: FAT read failed (blocknr 84779)
[35798.911717] FAT: FAT read failed (blocknr 84779)
[35798.911731] FAT: FAT read failed (blocknr 84779)
[35798.911746] FAT: FAT read failed (blocknr 84779)
[35798.911760] FAT: FAT read failed (blocknr 84779)
[35798.911780] FAT: FAT read failed (blocknr 84779)
[35798.911808] FAT: FAT read failed (blocknr 84779)
[35798.911823] FAT: FAT read failed (blocknr 84779)
[35798.911837] FAT: FAT read failed (blocknr 84779)
[35798.911852] FAT: FAT read failed (blocknr 84779)
[35798.911866] FAT: FAT read failed (blocknr 84779)
[35798.911881] FAT: FAT read failed (blocknr 84779)
[35798.911895] FAT: FAT read failed (blocknr 84779)
[35798.911909] FAT: FAT read failed (blocknr 84779)
[35798.911927] FAT: FAT read failed (blocknr 84779)
[35798.911943] FAT: FAT read failed (blocknr 84779)
[35798.911958] FAT: FAT read failed (blocknr 84779)
[35798.911973] FAT: FAT read failed (blocknr 84779)
[35798.911987] FAT: FAT read failed (blocknr 84779)
[35798.912002] FAT: FAT read failed (blocknr 84779)
[35798.912016] FAT: FAT read failed (blocknr 84779)
[35798.912030] FAT: FAT read failed (blocknr 84779)
[35798.912045] FAT: FAT read failed (blocknr 84779)
[35798.912062] FAT: FAT read failed (blocknr 84779)
[35798.912078] FAT: FAT read failed (blocknr 84779)
[35798.912093] FAT: FAT read failed (blocknr 84779)
[35798.912107] FAT: FAT read failed (blocknr 84779)
[35798.912122] FAT: FAT read failed (blocknr 84779)
[35798.912136] FAT: FAT read failed (blocknr 84779)
[35798.912150] FAT: FAT read failed (blocknr 84779)
[35798.912165] FAT: FAT read failed (blocknr 84779)
[35798.912179] FAT: FAT read failed (blocknr 84779)
[35798.912196] FAT: FAT read failed (blocknr 84779)
[35798.912213] FAT: FAT read failed (blocknr 84779)
[35798.912227] FAT: FAT read failed (blocknr 84779)
[35798.912241] FAT: FAT read failed (blocknr 84779)
[35798.912256] FAT: FAT read failed (blocknr 84779)
[35798.912270] FAT: FAT read failed (blocknr 84779)
[35798.912285] FAT: FAT read failed (blocknr 84779)
[35798.912299] FAT: FAT read failed (blocknr 84779)
[35798.912313] FAT: FAT read failed (blocknr 84779)
[35798.912330] FAT: FAT read failed (blocknr 84779)
[35798.912346] FAT: FAT read failed (blocknr 84779)
[35798.912361] FAT: FAT read failed (blocknr 84779)
[35798.912375] FAT: FAT read failed (blocknr 84779)
[35798.912390] FAT: FAT read failed (blocknr 84779)
[35798.912404] FAT: FAT read failed (blocknr 84779)
[35798.912418] FAT: FAT read failed (blocknr 84779)
[35798.912433] FAT: FAT read failed (blocknr 84779)
[35798.912447] FAT: FAT read failed (blocknr 84779)
[35798.912464] FAT: FAT read failed (blocknr 84779)
[35798.912480] FAT: FAT read failed (blocknr 84779)
[35798.912495] FAT: FAT read failed (blocknr 84779)
[35798.912509] FAT: FAT read failed (blocknr 84779)
[35798.912524] FAT: FAT read failed (blocknr 84779)
[35798.912538] FAT: FAT read failed (blocknr 84779)
[35798.912552] FAT: FAT read failed (blocknr 84779)
[35798.912567] FAT: FAT read failed (blocknr 84779)
[35798.912581] FAT: FAT read failed (blocknr 84779)
[35798.912598] FAT: FAT read failed (blocknr 84779)
[35798.912615] FAT: FAT read failed (blocknr 84779)
[35798.912629] FAT: FAT read failed (blocknr 84779)
[35798.912644] FAT: FAT read failed (blocknr 84779)
[35798.912658] FAT: FAT read failed (blocknr 84779)
[35798.912673] FAT: FAT read failed (blocknr 84779)
[35798.912687] FAT: FAT read failed (blocknr 84779)
[35798.912701] FAT: FAT read failed (blocknr 84779)
[35798.912716] FAT: FAT read failed (blocknr 84779)
[35798.912733] FAT: FAT read failed (blocknr 84779)
[35798.912749] FAT: FAT read failed (blocknr 84779)
[35798.912764] FAT: FAT read failed (blocknr 84779)
[35798.912778] FAT: FAT read failed (blocknr 84779)
[35798.912793] FAT: FAT read failed (blocknr 84779)
[35798.912807] FAT: FAT read failed (blocknr 84779)
[35798.912822] FAT: FAT read failed (blocknr 84779)
[35798.912836] FAT: FAT read failed (blocknr 84779)
[35798.912851] FAT: FAT read failed (blocknr 84779)
[35798.912868] FAT: FAT read failed (blocknr 84779)
[35798.912894] FAT: FAT read failed (blocknr 84779)
[35798.912909] FAT: FAT read failed (blocknr 84779)
[35798.912924] FAT: FAT read failed (blocknr 84779)
[35798.912940] FAT: FAT read failed (blocknr 84779)
[35798.912954] FAT: FAT read failed (blocknr 84779)
[35798.912969] FAT: FAT read failed (blocknr 84779)
[35798.912983] FAT: FAT read failed (blocknr 84779)
[35798.914625] FAT: FAT read failed (blocknr 84779)
[35798.914694] FAT: FAT read failed (blocknr 84779)
[35798.914725] FAT: FAT read failed (blocknr 84779)
[35798.914752] FAT: FAT read failed (blocknr 84779)
[35798.914778] FAT: FAT read failed (blocknr 84779)
[35798.914805] FAT: FAT read failed (blocknr 84779)
[35798.914832] FAT: FAT read failed (blocknr 84779)
[35798.914859] FAT: FAT read failed (blocknr 84779)
[35798.914885] FAT: FAT read failed (blocknr 84779)
[35798.914911] FAT: FAT read failed (blocknr 84779)
[35798.914942] FAT: FAT read failed (blocknr 84779)
[35798.914969] FAT: FAT read failed (blocknr 84779)
[35798.914996] FAT: FAT read failed (blocknr 84779)
[35798.915022] FAT: FAT read failed (blocknr 84779)
[35798.915048] FAT: FAT read failed (blocknr 84779)
[35798.915074] FAT: FAT read failed (blocknr 84779)
[35798.915101] FAT: FAT read failed (blocknr 84779)
[35798.915127] FAT: FAT read failed (blocknr 84779)
[35798.918217] FAT: Directory bread(block 34669432) failed
[35798.918248] FAT: Directory bread(block 34669433) failed
[35798.918277] FAT: Directory bread(block 34669434) failed
[35798.918304] FAT: Directory bread(block 34669435) failed
[35798.918332] FAT: Directory bread(block 34669436) failed
[35798.918359] FAT: Directory bread(block 34669437) failed
[35798.918387] FAT: Directory bread(block 34669438) failed
[35798.918414] FAT: Directory bread(block 34669439) failed
[35798.918442] FAT: Directory bread(block 34669440) failed
[35798.918470] FAT: Directory bread(block 34669441) failed
[35798.918497] FAT: Directory bread(block 34669442) failed
[35798.918525] FAT: Directory bread(block 34669443) failed
[35798.918552] FAT: Directory bread(block 34669444) failed
[35798.918580] FAT: Directory bread(block 34669445) failed
[35798.918608] FAT: Directory bread(block 34669446) failed
[35798.918636] FAT: Directory bread(block 34669447) failed
[35798.918663] FAT: Directory bread(block 34669448) failed
[35798.918691] FAT: Directory bread(block 34669449) failed
[35798.918718] FAT: Directory bread(block 34669450) failed
[35798.918746] FAT: Directory bread(block 34669451) failed
[35798.918773] FAT: Directory bread(block 34669452) failed
[35798.918800] FAT: Directory bread(block 34669453) failed
[35798.918828] FAT: Directory bread(block 34669454) failed
[35798.918856] FAT: Directory bread(block 34669455) failed
[35798.918883] FAT: Directory bread(block 34669456) failed
[35798.918911] FAT: Directory bread(block 34669457) failed
[35798.918938] FAT: Directory bread(block 34669458) failed
[35798.918966] FAT: Directory bread(block 34669459) failed
[35798.918993] FAT: Directory bread(block 34669460) failed
[35798.919021] FAT: Directory bread(block 34669461) failed
[35798.919048] FAT: Directory bread(block 34669462) failed
[35798.919075] FAT: Directory bread(block 34669463) failed
[35798.919103] FAT: Directory bread(block 34669464) failed
[35798.919132] FAT: Directory bread(block 34669465) failed
[35798.919160] FAT: Directory bread(block 34669466) failed
[35798.919187] FAT: Directory bread(block 34669467) failed
[35798.919215] FAT: Directory bread(block 34669468) failed
[35798.919243] FAT: Directory bread(block 34669469) failed
[35798.919271] FAT: Directory bread(block 34669470) failed
[35798.919298] FAT: Directory bread(block 34669471) failed
[35798.919326] FAT: Directory bread(block 34669472) failed
[35798.919354] FAT: Directory bread(block 34669473) failed
[35798.919381] FAT: Directory bread(block 34669474) failed
[35798.919408] FAT: Directory bread(block 34669475) failed
[35798.919436] FAT: Directory bread(block 34669476) failed
[35798.919464] FAT: Directory bread(block 34669477) failed
[35798.919491] FAT: Directory bread(block 34669478) failed
[35798.919518] FAT: Directory bread(block 34669479) failed
[35798.919546] FAT: Directory bread(block 34669480) failed
[35798.919573] FAT: Directory bread(block 34669481) failed
[35798.919602] FAT: Directory bread(block 34669482) failed
[35798.919629] FAT: Directory bread(block 34669483) failed
[35798.919658] FAT: Directory bread(block 34669484) failed
[35798.919686] FAT: Directory bread(block 34669485) failed
[35798.919713] FAT: Directory bread(block 34669486) failed
[35798.919741] FAT: Directory bread(block 34669487) failed
[35798.919768] FAT: Directory bread(block 34669488) failed
[35798.919796] FAT: Directory bread(block 34669489) failed
[35798.919823] FAT: Directory bread(block 34669490) failed
[35798.919851] FAT: Directory bread(block 34669491) failed
[35798.919878] FAT: Directory bread(block 34669492) failed
[35798.919906] FAT: Directory bread(block 34669493) failed
[35798.919933] FAT: Directory bread(block 34669494) failed
[35798.919961] FAT: Directory bread(block 34669495) failed
[35798.925079] __ratelimit: 1606 callbacks suppressed
[35798.925090] Buffer I/O error on device sdc1, logical block 679839291
[35798.925101] lost page write due to I/O error on sdc1
[35798.925170] FAT: unable to read inode block for updating (i_pos 10877428669)
[35799.369052] usb 7-4: new high speed USB device using ehci_hcd and address 17
[35799.501837] usb 7-4: configuration #1 chosen from 1 choice
[35799.503304] scsi19 : SCSI emulation for USB Mass Storage devices
[35799.506078] usb-storage: device found at 17
[35799.506090] usb-storage: waiting for device to settle before scanning
[35804.504438] usb-storage: device scan complete
[35804.506672] scsi 19:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[35804.510232] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.510759] sd 19:0:0:0: [sdb] Write Protect is off
[35804.510771] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.510779] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511470] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.511967] sd 19:0:0:0: [sdb] Write Protect is off
[35804.511976] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.511984] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511997]  sdb: sdb1
[35804.540663] sd 19:0:0:0: [sdb] Attached SCSI disk
[35804.540881] sd 19:0:0:0: Attached scsi generic sg2 type 0
[35816.546231] ath5k phy0: unsupported jumbo
[36066.307003] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=83.157.171.11 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=108 ID=29854 PROTO=UDP SPT=55934 DPT=49786 LEN=111
```

---

### Post by Rocket2DMn on 2009-04-25
Hmm, this could be any number of things.  It is most likely either a kernel bug, a bad filesystem, or a failing hard drive.  Does the problem go away if you do
```
sudo rmmod ehci_hcd
```
You will only be able to access the drive at USB 1.1 speed, but we can at least tell if the problem goes away.

---

### Post by qjmoss on 2009-04-25
Well i'd hope it's not a failing harddrive, i've only had it for a month...



and I pasted it.


Error seems to still be here.

---

### Post by qjmoss on 2009-04-25
New output


```
[35798.908805] FAT: FAT read failed (blocknr 84779)
[35798.908819] FAT: FAT read failed (blocknr 84779)
[35798.908837] FAT: FAT read failed (blocknr 84779)
[35798.908854] FAT: FAT read failed (blocknr 84779)
[35798.908869] FAT: FAT read failed (blocknr 84779)
[35798.908883] FAT: FAT read failed (blocknr 84779)
[35798.908898] FAT: FAT read failed (blocknr 84779)
[35798.908912] FAT: FAT read failed (blocknr 84779)
[35798.908927] FAT: FAT read failed (blocknr 84779)
[35798.908941] FAT: FAT read failed (blocknr 84779)
[35798.908955] FAT: FAT read failed (blocknr 84779)
[35798.908973] FAT: FAT read failed (blocknr 84779)
[35798.908991] FAT: FAT read failed (blocknr 84779)
[35798.909036] FAT: FAT read failed (blocknr 84779)
[35798.909051] FAT: FAT read failed (blocknr 84779)
[35798.909065] FAT: FAT read failed (blocknr 84779)
[35798.909080] FAT: FAT read failed (blocknr 84779)
[35798.909094] FAT: FAT read failed (blocknr 84779)
[35798.909108] FAT: FAT read failed (blocknr 84779)
[35798.909123] FAT: FAT read failed (blocknr 84779)
[35798.909141] FAT: FAT read failed (blocknr 84779)
[35798.909157] FAT: FAT read failed (blocknr 84779)
[35798.909172] FAT: FAT read failed (blocknr 84779)
[35798.909186] FAT: FAT read failed (blocknr 84779)
[35798.909201] FAT: FAT read failed (blocknr 84779)
[35798.909215] FAT: FAT read failed (blocknr 84779)
[35798.909229] FAT: FAT read failed (blocknr 84779)
[35798.909244] FAT: FAT read failed (blocknr 84779)
[35798.909258] FAT: FAT read failed (blocknr 84779)
[35798.909275] FAT: FAT read failed (blocknr 84779)
[35798.909292] FAT: FAT read failed (blocknr 84779)
[35798.909306] FAT: FAT read failed (blocknr 84779)
[35798.909321] FAT: FAT read failed (blocknr 84779)
[35798.909335] FAT: FAT read failed (blocknr 84779)
[35798.909350] FAT: FAT read failed (blocknr 84779)
[35798.909364] FAT: FAT read failed (blocknr 84779)
[35798.909379] FAT: FAT read failed (blocknr 84779)
[35798.909393] FAT: FAT read failed (blocknr 84779)
[35798.909410] FAT: FAT read failed (blocknr 84779)
[35798.909426] FAT: FAT read failed (blocknr 84779)
[35798.909441] FAT: FAT read failed (blocknr 84779)
[35798.909456] FAT: FAT read failed (blocknr 84779)
[35798.909470] FAT: FAT read failed (blocknr 84779)
[35798.909485] FAT: FAT read failed (blocknr 84779)
[35798.909501] FAT: FAT read failed (blocknr 84779)
[35798.909516] FAT: FAT read failed (blocknr 84779)
[35798.909530] FAT: FAT read failed (blocknr 84779)
[35798.909549] FAT: FAT read failed (blocknr 84779)
[35798.909567] FAT: FAT read failed (blocknr 84779)
[35798.909582] FAT: FAT read failed (blocknr 84779)
[35798.909596] FAT: FAT read failed (blocknr 84779)
[35798.909611] FAT: FAT read failed (blocknr 84779)
[35798.909626] FAT: FAT read failed (blocknr 84779)
[35798.909640] FAT: FAT read failed (blocknr 84779)
[35798.909656] FAT: FAT read failed (blocknr 84779)
[35798.909671] FAT: FAT read failed (blocknr 84779)
[35798.909688] FAT: FAT read failed (blocknr 84779)
[35798.909706] FAT: FAT read failed (blocknr 84779)
[35798.909722] FAT: FAT read failed (blocknr 84779)
[35798.909736] FAT: FAT read failed (blocknr 84779)
[35798.909751] FAT: FAT read failed (blocknr 84779)
[35798.909765] FAT: FAT read failed (blocknr 84779)
[35798.909780] FAT: FAT read failed (blocknr 84779)
[35798.909794] FAT: FAT read failed (blocknr 84779)
[35798.909808] FAT: FAT read failed (blocknr 84779)
[35798.909829] FAT: FAT read failed (blocknr 84779)
[35798.909847] FAT: FAT read failed (blocknr 84779)
[35798.909863] FAT: FAT read failed (blocknr 84779)
[35798.909877] FAT: FAT read failed (blocknr 84779)
[35798.909891] FAT: FAT read failed (blocknr 84779)
[35798.909906] FAT: FAT read failed (blocknr 84779)
[35798.909920] FAT: FAT read failed (blocknr 84779)
[35798.909934] FAT: FAT read failed (blocknr 84779)
[35798.909949] FAT: FAT read failed (blocknr 84779)
[35798.909966] FAT: FAT read failed (blocknr 84779)
[35798.909983] FAT: FAT read failed (blocknr 84779)
[35798.909998] FAT: FAT read failed (blocknr 84779)
[35798.910012] FAT: FAT read failed (blocknr 84779)
[35798.910027] FAT: FAT read failed (blocknr 84779)
[35798.910041] FAT: FAT read failed (blocknr 84779)
[35798.910055] FAT: FAT read failed (blocknr 84779)
[35798.910070] FAT: FAT read failed (blocknr 84779)
[35798.910084] FAT: FAT read failed (blocknr 84779)
[35798.910101] FAT: FAT read failed (blocknr 84779)
[35798.910120] FAT: FAT read failed (blocknr 84779)
[35798.910135] FAT: FAT read failed (blocknr 84779)
[35798.910149] FAT: FAT read failed (blocknr 84779)
[35798.910163] FAT: FAT read failed (blocknr 84779)
[35798.910177] FAT: FAT read failed (blocknr 84779)
[35798.910192] FAT: FAT read failed (blocknr 84779)
[35798.910206] FAT: FAT read failed (blocknr 84779)
[35798.910221] FAT: FAT read failed (blocknr 84779)
[35798.910238] FAT: FAT read failed (blocknr 84779)
[35798.910255] FAT: FAT read failed (blocknr 84779)
[35798.910270] FAT: FAT read failed (blocknr 84779)
[35798.910284] FAT: FAT read failed (blocknr 84779)
[35798.910299] FAT: FAT read failed (blocknr 84779)
[35798.910313] FAT: FAT read failed (blocknr 84779)
[35798.910327] FAT: FAT read failed (blocknr 84779)
[35798.910342] FAT: FAT read failed (blocknr 84779)
[35798.910356] FAT: FAT read failed (blocknr 84779)
[35798.910373] FAT: FAT read failed (blocknr 84779)
[35798.910392] FAT: FAT read failed (blocknr 84779)
[35798.910408] FAT: FAT read failed (blocknr 84779)
[35798.910422] FAT: FAT read failed (blocknr 84779)
[35798.910437] FAT: FAT read failed (blocknr 84779)
[35798.910451] FAT: FAT read failed (blocknr 84779)
[35798.910466] FAT: FAT read failed (blocknr 84779)
[35798.910480] FAT: FAT read failed (blocknr 84779)
[35798.910494] FAT: FAT read failed (blocknr 84779)
[35798.910512] FAT: FAT read failed (blocknr 84779)
[35798.910530] FAT: FAT read failed (blocknr 84779)
[35798.910546] FAT: FAT read failed (blocknr 84779)
[35798.910560] FAT: FAT read failed (blocknr 84779)
[35798.910574] FAT: FAT read failed (blocknr 84779)
[35798.910589] FAT: FAT read failed (blocknr 84779)
[35798.910603] FAT: FAT read failed (blocknr 84779)
[35798.910617] FAT: FAT read failed (blocknr 84779)
[35798.910632] FAT: FAT read failed (blocknr 84779)
[35798.910649] FAT: FAT read failed (blocknr 84779)
[35798.910677] FAT: FAT read failed (blocknr 84779)
[35798.910692] FAT: FAT read failed (blocknr 84779)
[35798.910706] FAT: FAT read failed (blocknr 84779)
[35798.910721] FAT: FAT read failed (blocknr 84779)
[35798.910735] FAT: FAT read failed (blocknr 84779)
[35798.910750] FAT: FAT read failed (blocknr 84779)
[35798.910764] FAT: FAT read failed (blocknr 84779)
[35798.910778] FAT: FAT read failed (blocknr 84779)
[35798.910796] FAT: FAT read failed (blocknr 84779)
[35798.910812] FAT: FAT read failed (blocknr 84779)
[35798.910826] FAT: FAT read failed (blocknr 84779)
[35798.910841] FAT: FAT read failed (blocknr 84779)
[35798.910855] FAT: FAT read failed (blocknr 84779)
[35798.910870] FAT: FAT read failed (blocknr 84779)
[35798.910884] FAT: FAT read failed (blocknr 84779)
[35798.910898] FAT: FAT read failed (blocknr 84779)
[35798.910912] FAT: FAT read failed (blocknr 84779)
[35798.910930] FAT: FAT read failed (blocknr 84779)
[35798.910946] FAT: FAT read failed (blocknr 84779)
[35798.910960] FAT: FAT read failed (blocknr 84779)
[35798.910975] FAT: FAT read failed (blocknr 84779)
[35798.910989] FAT: FAT read failed (blocknr 84779)
[35798.911003] FAT: FAT read failed (blocknr 84779)
[35798.911018] FAT: FAT read failed (blocknr 84779)
[35798.911032] FAT: FAT read failed (blocknr 84779)
[35798.911046] FAT: FAT read failed (blocknr 84779)
[35798.911064] FAT: FAT read failed (blocknr 84779)
[35798.911080] FAT: FAT read failed (blocknr 84779)
[35798.911094] FAT: FAT read failed (blocknr 84779)
[35798.911108] FAT: FAT read failed (blocknr 84779)
[35798.911123] FAT: FAT read failed (blocknr 84779)
[35798.911171] FAT: FAT read failed (blocknr 84779)
[35798.911185] FAT: FAT read failed (blocknr 84779)
[35798.911200] FAT: FAT read failed (blocknr 84779)
[35798.911214] FAT: FAT read failed (blocknr 84779)
[35798.911232] FAT: FAT read failed (blocknr 84779)
[35798.911249] FAT: FAT read failed (blocknr 84779)
[35798.911265] FAT: FAT read failed (blocknr 84779)
[35798.911279] FAT: FAT read failed (blocknr 84779)
[35798.911294] FAT: FAT read failed (blocknr 84779)
[35798.911309] FAT: FAT read failed (blocknr 84779)
[35798.911324] FAT: FAT read failed (blocknr 84779)
[35798.911338] FAT: FAT read failed (blocknr 84779)
[35798.911353] FAT: FAT read failed (blocknr 84779)
[35798.911370] FAT: FAT read failed (blocknr 84779)
[35798.911387] FAT: FAT read failed (blocknr 84779)
[35798.911402] FAT: FAT read failed (blocknr 84779)
[35798.911417] FAT: FAT read failed (blocknr 84779)
[35798.911432] FAT: FAT read failed (blocknr 84779)
[35798.911447] FAT: FAT read failed (blocknr 84779)
[35798.911461] FAT: FAT read failed (blocknr 84779)
[35798.911476] FAT: FAT read failed (blocknr 84779)
[35798.911491] FAT: FAT read failed (blocknr 84779)
[35798.911508] FAT: FAT read failed (blocknr 84779)
[35798.911524] FAT: FAT read failed (blocknr 84779)
[35798.911539] FAT: FAT read failed (blocknr 84779)
[35798.911553] FAT: FAT read failed (blocknr 84779)
[35798.911568] FAT: FAT read failed (blocknr 84779)
[35798.911582] FAT: FAT read failed (blocknr 84779)
[35798.911597] FAT: FAT read failed (blocknr 84779)
[35798.911611] FAT: FAT read failed (blocknr 84779)
[35798.911626] FAT: FAT read failed (blocknr 84779)
[35798.911643] FAT: FAT read failed (blocknr 84779)
[35798.911659] FAT: FAT read failed (blocknr 84779)
[35798.911674] FAT: FAT read failed (blocknr 84779)
[35798.911688] FAT: FAT read failed (blocknr 84779)
[35798.911702] FAT: FAT read failed (blocknr 84779)
[35798.911717] FAT: FAT read failed (blocknr 84779)
[35798.911731] FAT: FAT read failed (blocknr 84779)
[35798.911746] FAT: FAT read failed (blocknr 84779)
[35798.911760] FAT: FAT read failed (blocknr 84779)
[35798.911780] FAT: FAT read failed (blocknr 84779)
[35798.911808] FAT: FAT read failed (blocknr 84779)
[35798.911823] FAT: FAT read failed (blocknr 84779)
[35798.911837] FAT: FAT read failed (blocknr 84779)
[35798.911852] FAT: FAT read failed (blocknr 84779)
[35798.911866] FAT: FAT read failed (blocknr 84779)
[35798.911881] FAT: FAT read failed (blocknr 84779)
[35798.911895] FAT: FAT read failed (blocknr 84779)
[35798.911909] FAT: FAT read failed (blocknr 84779)
[35798.911927] FAT: FAT read failed (blocknr 84779)
[35798.911943] FAT: FAT read failed (blocknr 84779)
[35798.911958] FAT: FAT read failed (blocknr 84779)
[35798.911973] FAT: FAT read failed (blocknr 84779)
[35798.911987] FAT: FAT read failed (blocknr 84779)
[35798.912002] FAT: FAT read failed (blocknr 84779)
[35798.912016] FAT: FAT read failed (blocknr 84779)
[35798.912030] FAT: FAT read failed (blocknr 84779)
[35798.912045] FAT: FAT read failed (blocknr 84779)
[35798.912062] FAT: FAT read failed (blocknr 84779)
[35798.912078] FAT: FAT read failed (blocknr 84779)
[35798.912093] FAT: FAT read failed (blocknr 84779)
[35798.912107] FAT: FAT read failed (blocknr 84779)
[35798.912122] FAT: FAT read failed (blocknr 84779)
[35798.912136] FAT: FAT read failed (blocknr 84779)
[35798.912150] FAT: FAT read failed (blocknr 84779)
[35798.912165] FAT: FAT read failed (blocknr 84779)
[35798.912179] FAT: FAT read failed (blocknr 84779)
[35798.912196] FAT: FAT read failed (blocknr 84779)
[35798.912213] FAT: FAT read failed (blocknr 84779)
[35798.912227] FAT: FAT read failed (blocknr 84779)
[35798.912241] FAT: FAT read failed (blocknr 84779)
[35798.912256] FAT: FAT read failed (blocknr 84779)
[35798.912270] FAT: FAT read failed (blocknr 84779)
[35798.912285] FAT: FAT read failed (blocknr 84779)
[35798.912299] FAT: FAT read failed (blocknr 84779)
[35798.912313] FAT: FAT read failed (blocknr 84779)
[35798.912330] FAT: FAT read failed (blocknr 84779)
[35798.912346] FAT: FAT read failed (blocknr 84779)
[35798.912361] FAT: FAT read failed (blocknr 84779)
[35798.912375] FAT: FAT read failed (blocknr 84779)
[35798.912390] FAT: FAT read failed (blocknr 84779)
[35798.912404] FAT: FAT read failed (blocknr 84779)
[35798.912418] FAT: FAT read failed (blocknr 84779)
[35798.912433] FAT: FAT read failed (blocknr 84779)
[35798.912447] FAT: FAT read failed (blocknr 84779)
[35798.912464] FAT: FAT read failed (blocknr 84779)
[35798.912480] FAT: FAT read failed (blocknr 84779)
[35798.912495] FAT: FAT read failed (blocknr 84779)
[35798.912509] FAT: FAT read failed (blocknr 84779)
[35798.912524] FAT: FAT read failed (blocknr 84779)
[35798.912538] FAT: FAT read failed (blocknr 84779)
[35798.912552] FAT: FAT read failed (blocknr 84779)
[35798.912567] FAT: FAT read failed (blocknr 84779)
[35798.912581] FAT: FAT read failed (blocknr 84779)
[35798.912598] FAT: FAT read failed (blocknr 84779)
[35798.912615] FAT: FAT read failed (blocknr 84779)
[35798.912629] FAT: FAT read failed (blocknr 84779)
[35798.912644] FAT: FAT read failed (blocknr 84779)
[35798.912658] FAT: FAT read failed (blocknr 84779)
[35798.912673] FAT: FAT read failed (blocknr 84779)
[35798.912687] FAT: FAT read failed (blocknr 84779)
[35798.912701] FAT: FAT read failed (blocknr 84779)
[35798.912716] FAT: FAT read failed (blocknr 84779)
[35798.912733] FAT: FAT read failed (blocknr 84779)
[35798.912749] FAT: FAT read failed (blocknr 84779)
[35798.912764] FAT: FAT read failed (blocknr 84779)
[35798.912778] FAT: FAT read failed (blocknr 84779)
[35798.912793] FAT: FAT read failed (blocknr 84779)
[35798.912807] FAT: FAT read failed (blocknr 84779)
[35798.912822] FAT: FAT read failed (blocknr 84779)
[35798.912836] FAT: FAT read failed (blocknr 84779)
[35798.912851] FAT: FAT read failed (blocknr 84779)
[35798.912868] FAT: FAT read failed (blocknr 84779)
[35798.912894] FAT: FAT read failed (blocknr 84779)
[35798.912909] FAT: FAT read failed (blocknr 84779)
[35798.912924] FAT: FAT read failed (blocknr 84779)
[35798.912940] FAT: FAT read failed (blocknr 84779)
[35798.912954] FAT: FAT read failed (blocknr 84779)
[35798.912969] FAT: FAT read failed (blocknr 84779)
[35798.912983] FAT: FAT read failed (blocknr 84779)
[35798.914625] FAT: FAT read failed (blocknr 84779)
[35798.914694] FAT: FAT read failed (blocknr 84779)
[35798.914725] FAT: FAT read failed (blocknr 84779)
[35798.914752] FAT: FAT read failed (blocknr 84779)
[35798.914778] FAT: FAT read failed (blocknr 84779)
[35798.914805] FAT: FAT read failed (blocknr 84779)
[35798.914832] FAT: FAT read failed (blocknr 84779)
[35798.914859] FAT: FAT read failed (blocknr 84779)
[35798.914885] FAT: FAT read failed (blocknr 84779)
[35798.914911] FAT: FAT read failed (blocknr 84779)
[35798.914942] FAT: FAT read failed (blocknr 84779)
[35798.914969] FAT: FAT read failed (blocknr 84779)
[35798.914996] FAT: FAT read failed (blocknr 84779)
[35798.915022] FAT: FAT read failed (blocknr 84779)
[35798.915048] FAT: FAT read failed (blocknr 84779)
[35798.915074] FAT: FAT read failed (blocknr 84779)
[35798.915101] FAT: FAT read failed (blocknr 84779)
[35798.915127] FAT: FAT read failed (blocknr 84779)
[35798.918217] FAT: Directory bread(block 34669432) failed
[35798.918248] FAT: Directory bread(block 34669433) failed
[35798.918277] FAT: Directory bread(block 34669434) failed
[35798.918304] FAT: Directory bread(block 34669435) failed
[35798.918332] FAT: Directory bread(block 34669436) failed
[35798.918359] FAT: Directory bread(block 34669437) failed
[35798.918387] FAT: Directory bread(block 34669438) failed
[35798.918414] FAT: Directory bread(block 34669439) failed
[35798.918442] FAT: Directory bread(block 34669440) failed
[35798.918470] FAT: Directory bread(block 34669441) failed
[35798.918497] FAT: Directory bread(block 34669442) failed
[35798.918525] FAT: Directory bread(block 34669443) failed
[35798.918552] FAT: Directory bread(block 34669444) failed
[35798.918580] FAT: Directory bread(block 34669445) failed
[35798.918608] FAT: Directory bread(block 34669446) failed
[35798.918636] FAT: Directory bread(block 34669447) failed
[35798.918663] FAT: Directory bread(block 34669448) failed
[35798.918691] FAT: Directory bread(block 34669449) failed
[35798.918718] FAT: Directory bread(block 34669450) failed
[35798.918746] FAT: Directory bread(block 34669451) failed
[35798.918773] FAT: Directory bread(block 34669452) failed
[35798.918800] FAT: Directory bread(block 34669453) failed
[35798.918828] FAT: Directory bread(block 34669454) failed
[35798.918856] FAT: Directory bread(block 34669455) failed
[35798.918883] FAT: Directory bread(block 34669456) failed
[35798.918911] FAT: Directory bread(block 34669457) failed
[35798.918938] FAT: Directory bread(block 34669458) failed
[35798.918966] FAT: Directory bread(block 34669459) failed
[35798.918993] FAT: Directory bread(block 34669460) failed
[35798.919021] FAT: Directory bread(block 34669461) failed
[35798.919048] FAT: Directory bread(block 34669462) failed
[35798.919075] FAT: Directory bread(block 34669463) failed
[35798.919103] FAT: Directory bread(block 34669464) failed
[35798.919132] FAT: Directory bread(block 34669465) failed
[35798.919160] FAT: Directory bread(block 34669466) failed
[35798.919187] FAT: Directory bread(block 34669467) failed
[35798.919215] FAT: Directory bread(block 34669468) failed
[35798.919243] FAT: Directory bread(block 34669469) failed
[35798.919271] FAT: Directory bread(block 34669470) failed
[35798.919298] FAT: Directory bread(block 34669471) failed
[35798.919326] FAT: Directory bread(block 34669472) failed
[35798.919354] FAT: Directory bread(block 34669473) failed
[35798.919381] FAT: Directory bread(block 34669474) failed
[35798.919408] FAT: Directory bread(block 34669475) failed
[35798.919436] FAT: Directory bread(block 34669476) failed
[35798.919464] FAT: Directory bread(block 34669477) failed
[35798.919491] FAT: Directory bread(block 34669478) failed
[35798.919518] FAT: Directory bread(block 34669479) failed
[35798.919546] FAT: Directory bread(block 34669480) failed
[35798.919573] FAT: Directory bread(block 34669481) failed
[35798.919602] FAT: Directory bread(block 34669482) failed
[35798.919629] FAT: Directory bread(block 34669483) failed
[35798.919658] FAT: Directory bread(block 34669484) failed
[35798.919686] FAT: Directory bread(block 34669485) failed
[35798.919713] FAT: Directory bread(block 34669486) failed
[35798.919741] FAT: Directory bread(block 34669487) failed
[35798.919768] FAT: Directory bread(block 34669488) failed
[35798.919796] FAT: Directory bread(block 34669489) failed
[35798.919823] FAT: Directory bread(block 34669490) failed
[35798.919851] FAT: Directory bread(block 34669491) failed
[35798.919878] FAT: Directory bread(block 34669492) failed
[35798.919906] FAT: Directory bread(block 34669493) failed
[35798.919933] FAT: Directory bread(block 34669494) failed
[35798.919961] FAT: Directory bread(block 34669495) failed
[35798.925079] __ratelimit: 1606 callbacks suppressed
[35798.925090] Buffer I/O error on device sdc1, logical block 679839291
[35798.925101] lost page write due to I/O error on sdc1
[35798.925170] FAT: unable to read inode block for updating (i_pos 10877428669)
[35799.369052] usb 7-4: new high speed USB device using ehci_hcd and address 17
[35799.501837] usb 7-4: configuration #1 chosen from 1 choice
[35799.503304] scsi19 : SCSI emulation for USB Mass Storage devices
[35799.506078] usb-storage: device found at 17
[35799.506090] usb-storage: waiting for device to settle before scanning
[35804.504438] usb-storage: device scan complete
[35804.506672] scsi 19:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[35804.510232] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.510759] sd 19:0:0:0: [sdb] Write Protect is off
[35804.510771] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.510779] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511470] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.511967] sd 19:0:0:0: [sdb] Write Protect is off
[35804.511976] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.511984] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511997]  sdb: sdb1
[35804.540663] sd 19:0:0:0: [sdb] Attached SCSI disk
[35804.540881] sd 19:0:0:0: Attached scsi generic sg2 type 0
[35816.546231] ath5k phy0: unsupported jumbo
[36066.307003] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=83.157.171.11 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=108 ID=29854 PROTO=UDP SPT=55934 DPT=49786 LEN=111 
[36158.000087] CE: hpet increasing min_delta_ns to 15000 nsec
[36289.192131] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=91.153.200.10 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=113 ID=7426 PROTO=UDP SPT=63639 DPT=49786 LEN=111 
[36291.182588] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=119.246.78.87 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=47 ID=5255 PROTO=UDP SPT=12764 DPT=49786 LEN=111 
[36313.756970] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=203.218.223.100 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=114 ID=15391 PROTO=UDP SPT=19107 DPT=49786 LEN=55 
[36318.475670] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=123.139.61.159 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=110 ID=31171 PROTO=UDP SPT=21075 DPT=49786 LEN=55 
[36333.147312] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=71.103.49.170 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=110 ID=12307 PROTO=UDP SPT=50460 DPT=49786 LEN=111 
[36340.646009] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=97.85.176.56 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=112 ID=13387 PROTO=UDP SPT=20266 DPT=49786 LEN=55 
[36352.909419] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=220.136.47.196 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=105 ID=2414 PROTO=UDP SPT=20935 DPT=49786 LEN=55 
[36363.078463] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=62.43.68.145 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=110 ID=11795 PROTO=UDP SPT=13110 DPT=49786 LEN=55 
[36370.250832] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=200.104.49.33 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=117 ID=24672 PROTO=UDP SPT=21502 DPT=49786 LEN=274 
[36371.336018] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=122.123.0.112 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=105 ID=60581 PROTO=UDP SPT=25980 DPT=49786 LEN=55 
[36388.728427] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=85.229.184.249 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=104 ID=19849 PROTO=UDP SPT=17746 DPT=49786 LEN=274 
[36396.758575] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=24.207.140.186 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=112 ID=7417 PROTO=UDP SPT=20794 DPT=49786 LEN=55 
[36417.040679] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=58.252.51.84 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=111 ID=11352 PROTO=UDP SPT=59217 DPT=49786 LEN=274 
[36438.476937] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=221.0.104.129 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=47 ID=8302 PROTO=UDP SPT=26570 DPT=49786 LEN=55 
[36460.016634] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=71.68.223.237 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=115 ID=3595 PROTO=UDP SPT=11874 DPT=49786 LEN=55 
[36495.805511] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=118.160.232.222 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=106 ID=37112 PROTO=UDP SPT=20846 DPT=49786 LEN=274 
[36529.355859] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=222.150.45.179 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=106 ID=28092 PROTO=UDP SPT=20466 DPT=49786 LEN=55 
[36536.244482] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=83.7.189.167 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=111 ID=13434 PROTO=UDP SPT=18071 DPT=49786 LEN=274 
[36536.984805] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=201.92.37.200 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=108 ID=62278 PROTO=UDP SPT=59367 DPT=49786 LEN=55 
[36577.323643] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=61.62.95.174 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=113 ID=19467 PROTO=UDP SPT=12204 DPT=49786 LEN=274 
[36587.214080] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=79.114.218.188 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=109 ID=11529 PROTO=UDP SPT=21268 DPT=49786 LEN=55 
[36596.148606] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=219.211.238.178 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=107 ID=19932 PROTO=UDP SPT=40970 DPT=49786 LEN=111 
[36601.699723] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=76.65.19.44 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=115 ID=7664 PROTO=UDP SPT=23325 DPT=49786 LEN=55 
[36610.393726] ath5k phy0: unsupported jumbo
[36611.866877] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=122.133.47.197 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=107 ID=20849 PROTO=UDP SPT=22926 DPT=49786 LEN=55 
[36626.610609] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=70.81.209.50 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=109 ID=39827 PROTO=UDP SPT=14504 DPT=49786 LEN=274 
[36651.751753] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=88.195.69.184 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=110 ID=54883 PROTO=UDP SPT=21557 DPT=49786 LEN=274 
[36678.800488] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=125.224.119.145 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=105 ID=43960 PROTO=UDP SPT=8419 DPT=49786 LEN=274 
[36721.396878] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=64.17.89.10 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=110 ID=57658 PROTO=UDP SPT=41445 DPT=49786 LEN=274 
[36721.460434] ehci_hcd 0000:00:1d.7: remove, state 1
[36721.461430] usb usb7: USB disconnect, address 1
[36721.461440] usb 7-4: USB disconnect, address 17
[36721.475687] ehci_hcd 0000:00:1d.7: USB bus 7 deregistered
[36721.476880] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[36721.477883] ehci_hcd 0000:00:1a.7: remove, state 4
[36721.478791] usb usb3: USB disconnect, address 1
[36721.484002] ehci_hcd 0000:00:1a.7: USB bus 3 deregistered
[36721.484361] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[36721.776044] usb 5-2: new full speed USB device using uhci_hcd and address 4
[36721.938359] usb 5-2: configuration #1 chosen from 1 choice
[36721.946118] scsi20 : SCSI emulation for USB Mass Storage devices
[36721.946676] usb-storage: device found at 4
[36721.946680] usb-storage: waiting for device to settle before scanning
[36726.953079] usb-storage: device scan complete
[36726.956236] scsi 20:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[36726.969127] sd 20:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[36726.975381] sd 20:0:0:0: [sdb] Write Protect is off
[36726.975397] sd 20:0:0:0: [sdb] Mode Sense: 23 00 00 00
[36726.975404] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[36726.981215] sd 20:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[36726.985230] sd 20:0:0:0: [sdb] Write Protect is off
[36726.985246] sd 20:0:0:0: [sdb] Mode Sense: 23 00 00 00
[36726.985253] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[36726.985267]  sdb: sdb1
[36734.327601] sd 20:0:0:0: [sdb] Attached SCSI disk
[36734.327844] sd 20:0:0:0: Attached scsi generic sg2 type 0
[36802.171673] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=116.232.204.183 DST=192.168.2.21 LEN=126 TOS=0x00 PREC=0x20 TTL=112 ID=64418 PROTO=UDP SPT=18980 DPT=49786 LEN=106 
[36816.203075] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=118.173.67.27 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=94 ID=42853 PROTO=UDP SPT=8231 DPT=49786 LEN=111 
[36830.940052] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=190.58.69.237 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=111 ID=30154 PROTO=UDP SPT=28538 DPT=49786 LEN=111 
[36835.688831] ath5k phy0: unsupported jumbo
[36838.241893] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=152.7.16.122 DST=192.168.2.21 LEN=95 TOS=0x00 PREC=0x20 TTL=110 ID=26947 PROTO=UDP SPT=27289 DPT=49786 LEN=75 
quentin@quentin-laptop:~$
```

---

### Post by Rocket2DMn on 2009-04-25
Can you please post the output of the following commands while your drive is plugged in and mounted:
```
sudo fdisk -l
sudo blkid
mount
```

---

### Post by qjmoss on 2009-04-25
```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ab00e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19084   153292198+  83  Linux
/dev/sda2           19085       19457     2996122+   5  Extended
/dev/sda5           19085       19457     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)
quentin@quentin-laptop:~$ sudo blkid
/dev/sda1: UUID="3948b2c5-50be-45a3-aca8-c410caa2c0fa" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3ce52d21-57fa-4283-84b3-34a3bfcf52cb" 
/dev/sdb1: SEC_TYPE="msdos" UUID="92C6-0911" TYPE="vfat" LABEL="My Book"
```

---

### Post by qjmoss on 2009-04-25
```
sudo blkid
/dev/sda1: UUID="3948b2c5-50be-45a3-aca8-c410caa2c0fa" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3ce52d21-57fa-4283-84b3-34a3bfcf52cb" 
/dev/sdb1: SEC_TYPE="msdos" UUID="92C6-0911" TYPE="vfat" LABEL="My Book" 
quentin@quentin-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/quentin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=quentin)
/dev/sdb1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```

---

### Post by Rocket2DMn on 2009-04-25
Ok, can you please try to read/write from the folder on the drive again and see if it will let you.  Then post the "dmesg" output again.

Also, do you have any objection to reformatting this drive?  Is there anything currently on it that you need?  Have you already formatted it yourself, or did it come with FAT32 as the filesystem?  How large is this hard drive?

---

### Post by qjmoss on 2009-04-25
```
[35798.909229] FAT: FAT read failed (blocknr 84779)
[35798.909244] FAT: FAT read failed (blocknr 84779)
[35798.909258] FAT: FAT read failed (blocknr 84779)
[35798.909275] FAT: FAT read failed (blocknr 84779)
[35798.909292] FAT: FAT read failed (blocknr 84779)
[35798.909306] FAT: FAT read failed (blocknr 84779)
[35798.909321] FAT: FAT read failed (blocknr 84779)
[35798.909335] FAT: FAT read failed (blocknr 84779)
[35798.909350] FAT: FAT read failed (blocknr 84779)
[35798.909364] FAT: FAT read failed (blocknr 84779)
[35798.909379] FAT: FAT read failed (blocknr 84779)
[35798.909393] FAT: FAT read failed (blocknr 84779)
[35798.909410] FAT: FAT read failed (blocknr 84779)
[35798.909426] FAT: FAT read failed (blocknr 84779)
[35798.909441] FAT: FAT read failed (blocknr 84779)
[35798.909456] FAT: FAT read failed (blocknr 84779)
[35798.909470] FAT: FAT read failed (blocknr 84779)
[35798.909485] FAT: FAT read failed (blocknr 84779)
[35798.909501] FAT: FAT read failed (blocknr 84779)
[35798.909516] FAT: FAT read failed (blocknr 84779)
[35798.909530] FAT: FAT read failed (blocknr 84779)
[35798.909549] FAT: FAT read failed (blocknr 84779)
[35798.909567] FAT: FAT read failed (blocknr 84779)
[35798.909582] FAT: FAT read failed (blocknr 84779)
[35798.909596] FAT: FAT read failed (blocknr 84779)
[35798.909611] FAT: FAT read failed (blocknr 84779)
[35798.909626] FAT: FAT read failed (blocknr 84779)
[35798.909640] FAT: FAT read failed (blocknr 84779)
[35798.909656] FAT: FAT read failed (blocknr 84779)
[35798.909671] FAT: FAT read failed (blocknr 84779)
[35798.909688] FAT: FAT read failed (blocknr 84779)
[35798.909706] FAT: FAT read failed (blocknr 84779)
[35798.909722] FAT: FAT read failed (blocknr 84779)
[35798.909736] FAT: FAT read failed (blocknr 84779)
[35798.909751] FAT: FAT read failed (blocknr 84779)
[35798.909765] FAT: FAT read failed (blocknr 84779)
[35798.909780] FAT: FAT read failed (blocknr 84779)
[35798.909794] FAT: FAT read failed (blocknr 84779)
[35798.909808] FAT: FAT read failed (blocknr 84779)
[35798.909829] FAT: FAT read failed (blocknr 84779)
[35798.909847] FAT: FAT read failed (blocknr 84779)
[35798.909863] FAT: FAT read failed (blocknr 84779)
[35798.909877] FAT: FAT read failed (blocknr 84779)
[35798.909891] FAT: FAT read failed (blocknr 84779)
[35798.909906] FAT: FAT read failed (blocknr 84779)
[35798.909920] FAT: FAT read failed (blocknr 84779)
[35798.909934] FAT: FAT read failed (blocknr 84779)
[35798.909949] FAT: FAT read failed (blocknr 84779)
[35798.909966] FAT: FAT read failed (blocknr 84779)
[35798.909983] FAT: FAT read failed (blocknr 84779)
[35798.909998] FAT: FAT read failed (blocknr 84779)
[35798.910012] FAT: FAT read failed (blocknr 84779)
[35798.910027] FAT: FAT read failed (blocknr 84779)
[35798.910041] FAT: FAT read failed (blocknr 84779)
[35798.910055] FAT: FAT read failed (blocknr 84779)
[35798.910070] FAT: FAT read failed (blocknr 84779)
[35798.910084] FAT: FAT read failed (blocknr 84779)
[35798.910101] FAT: FAT read failed (blocknr 84779)
[35798.910120] FAT: FAT read failed (blocknr 84779)
[35798.910135] FAT: FAT read failed (blocknr 84779)
[35798.910149] FAT: FAT read failed (blocknr 84779)
[35798.910163] FAT: FAT read failed (blocknr 84779)
[35798.910177] FAT: FAT read failed (blocknr 84779)
[35798.910192] FAT: FAT read failed (blocknr 84779)
[35798.910206] FAT: FAT read failed (blocknr 84779)
[35798.910221] FAT: FAT read failed (blocknr 84779)
[35798.910238] FAT: FAT read failed (blocknr 84779)
[35798.910255] FAT: FAT read failed (blocknr 84779)
[35798.910270] FAT: FAT read failed (blocknr 84779)
[35798.910284] FAT: FAT read failed (blocknr 84779)
[35798.910299] FAT: FAT read failed (blocknr 84779)
[35798.910313] FAT: FAT read failed (blocknr 84779)
[35798.910327] FAT: FAT read failed (blocknr 84779)
[35798.910342] FAT: FAT read failed (blocknr 84779)
[35798.910356] FAT: FAT read failed (blocknr 84779)
[35798.910373] FAT: FAT read failed (blocknr 84779)
[35798.910392] FAT: FAT read failed (blocknr 84779)
[35798.910408] FAT: FAT read failed (blocknr 84779)
[35798.910422] FAT: FAT read failed (blocknr 84779)
[35798.910437] FAT: FAT read failed (blocknr 84779)
[35798.910451] FAT: FAT read failed (blocknr 84779)
[35798.910466] FAT: FAT read failed (blocknr 84779)
[35798.910480] FAT: FAT read failed (blocknr 84779)
[35798.910494] FAT: FAT read failed (blocknr 84779)
[35798.910512] FAT: FAT read failed (blocknr 84779)
[35798.910530] FAT: FAT read failed (blocknr 84779)
[35798.910546] FAT: FAT read failed (blocknr 84779)
[35798.910560] FAT: FAT read failed (blocknr 84779)
[35798.910574] FAT: FAT read failed (blocknr 84779)
[35798.910589] FAT: FAT read failed (blocknr 84779)
[35798.910603] FAT: FAT read failed (blocknr 84779)
[35798.910617] FAT: FAT read failed (blocknr 84779)
[35798.910632] FAT: FAT read failed (blocknr 84779)
[35798.910649] FAT: FAT read failed (blocknr 84779)
[35798.910677] FAT: FAT read failed (blocknr 84779)
[35798.910692] FAT: FAT read failed (blocknr 84779)
[35798.910706] FAT: FAT read failed (blocknr 84779)
[35798.910721] FAT: FAT read failed (blocknr 84779)
[35798.910735] FAT: FAT read failed (blocknr 84779)
[35798.910750] FAT: FAT read failed (blocknr 84779)
[35798.910764] FAT: FAT read failed (blocknr 84779)
[35798.910778] FAT: FAT read failed (blocknr 84779)
[35798.910796] FAT: FAT read failed (blocknr 84779)
[35798.910812] FAT: FAT read failed (blocknr 84779)
[35798.910826] FAT: FAT read failed (blocknr 84779)
[35798.910841] FAT: FAT read failed (blocknr 84779)
[35798.910855] FAT: FAT read failed (blocknr 84779)
[35798.910870] FAT: FAT read failed (blocknr 84779)
[35798.910884] FAT: FAT read failed (blocknr 84779)
[35798.910898] FAT: FAT read failed (blocknr 84779)
[35798.910912] FAT: FAT read failed (blocknr 84779)
[35798.910930] FAT: FAT read failed (blocknr 84779)
[35798.910946] FAT: FAT read failed (blocknr 84779)
[35798.910960] FAT: FAT read failed (blocknr 84779)
[35798.910975] FAT: FAT read failed (blocknr 84779)
[35798.910989] FAT: FAT read failed (blocknr 84779)
[35798.911003] FAT: FAT read failed (blocknr 84779)
[35798.911018] FAT: FAT read failed (blocknr 84779)
[35798.911032] FAT: FAT read failed (blocknr 84779)
[35798.911046] FAT: FAT read failed (blocknr 84779)
[35798.911064] FAT: FAT read failed (blocknr 84779)
[35798.911080] FAT: FAT read failed (blocknr 84779)
[35798.911094] FAT: FAT read failed (blocknr 84779)
[35798.911108] FAT: FAT read failed (blocknr 84779)
[35798.911123] FAT: FAT read failed (blocknr 84779)
[35798.911171] FAT: FAT read failed (blocknr 84779)
[35798.911185] FAT: FAT read failed (blocknr 84779)
[35798.911200] FAT: FAT read failed (blocknr 84779)
[35798.911214] FAT: FAT read failed (blocknr 84779)
[35798.911232] FAT: FAT read failed (blocknr 84779)
[35798.911249] FAT: FAT read failed (blocknr 84779)
[35798.911265] FAT: FAT read failed (blocknr 84779)
[35798.911279] FAT: FAT read failed (blocknr 84779)
[35798.911294] FAT: FAT read failed (blocknr 84779)
[35798.911309] FAT: FAT read failed (blocknr 84779)
[35798.911324] FAT: FAT read failed (blocknr 84779)
[35798.911338] FAT: FAT read failed (blocknr 84779)
[35798.911353] FAT: FAT read failed (blocknr 84779)
[35798.911370] FAT: FAT read failed (blocknr 84779)
[35798.911387] FAT: FAT read failed (blocknr 84779)
[35798.911402] FAT: FAT read failed (blocknr 84779)
[35798.911417] FAT: FAT read failed (blocknr 84779)
[35798.911432] FAT: FAT read failed (blocknr 84779)
[35798.911447] FAT: FAT read failed (blocknr 84779)
[35798.911461] FAT: FAT read failed (blocknr 84779)
[35798.911476] FAT: FAT read failed (blocknr 84779)
[35798.911491] FAT: FAT read failed (blocknr 84779)
[35798.911508] FAT: FAT read failed (blocknr 84779)
[35798.911524] FAT: FAT read failed (blocknr 84779)
[35798.911539] FAT: FAT read failed (blocknr 84779)
[35798.911553] FAT: FAT read failed (blocknr 84779)
[35798.911568] FAT: FAT read failed (blocknr 84779)
[35798.911582] FAT: FAT read failed (blocknr 84779)
[35798.911597] FAT: FAT read failed (blocknr 84779)
[35798.911611] FAT: FAT read failed (blocknr 84779)
[35798.911626] FAT: FAT read failed (blocknr 84779)
[35798.911643] FAT: FAT read failed (blocknr 84779)
[35798.911659] FAT: FAT read failed (blocknr 84779)
[35798.911674] FAT: FAT read failed (blocknr 84779)
[35798.911688] FAT: FAT read failed (blocknr 84779)
[35798.911702] FAT: FAT read failed (blocknr 84779)
[35798.911717] FAT: FAT read failed (blocknr 84779)
[35798.911731] FAT: FAT read failed (blocknr 84779)
[35798.911746] FAT: FAT read failed (blocknr 84779)
[35798.911760] FAT: FAT read failed (blocknr 84779)
[35798.911780] FAT: FAT read failed (blocknr 84779)
[35798.911808] FAT: FAT read failed (blocknr 84779)
[35798.911823] FAT: FAT read failed (blocknr 84779)
[35798.911837] FAT: FAT read failed (blocknr 84779)
[35798.911852] FAT: FAT read failed (blocknr 84779)
[35798.911866] FAT: FAT read failed (blocknr 84779)
[35798.911881] FAT: FAT read failed (blocknr 84779)
[35798.911895] FAT: FAT read failed (blocknr 84779)
[35798.911909] FAT: FAT read failed (blocknr 84779)
[35798.911927] FAT: FAT read failed (blocknr 84779)
[35798.911943] FAT: FAT read failed (blocknr 84779)
[35798.911958] FAT: FAT read failed (blocknr 84779)
[35798.911973] FAT: FAT read failed (blocknr 84779)
[35798.911987] FAT: FAT read failed (blocknr 84779)
[35798.912002] FAT: FAT read failed (blocknr 84779)
[35798.912016] FAT: FAT read failed (blocknr 84779)
[35798.912030] FAT: FAT read failed (blocknr 84779)
[35798.912045] FAT: FAT read failed (blocknr 84779)
[35798.912062] FAT: FAT read failed (blocknr 84779)
[35798.912078] FAT: FAT read failed (blocknr 84779)
[35798.912093] FAT: FAT read failed (blocknr 84779)
[35798.912107] FAT: FAT read failed (blocknr 84779)
[35798.912122] FAT: FAT read failed (blocknr 84779)
[35798.912136] FAT: FAT read failed (blocknr 84779)
[35798.912150] FAT: FAT read failed (blocknr 84779)
[35798.912165] FAT: FAT read failed (blocknr 84779)
[35798.912179] FAT: FAT read failed (blocknr 84779)
[35798.912196] FAT: FAT read failed (blocknr 84779)
[35798.912213] FAT: FAT read failed (blocknr 84779)
[35798.912227] FAT: FAT read failed (blocknr 84779)
[35798.912241] FAT: FAT read failed (blocknr 84779)
[35798.912256] FAT: FAT read failed (blocknr 84779)
[35798.912270] FAT: FAT read failed (blocknr 84779)
[35798.912285] FAT: FAT read failed (blocknr 84779)
[35798.912299] FAT: FAT read failed (blocknr 84779)
[35798.912313] FAT: FAT read failed (blocknr 84779)
[35798.912330] FAT: FAT read failed (blocknr 84779)
[35798.912346] FAT: FAT read failed (blocknr 84779)
[35798.912361] FAT: FAT read failed (blocknr 84779)
[35798.912375] FAT: FAT read failed (blocknr 84779)
[35798.912390] FAT: FAT read failed (blocknr 84779)
[35798.912404] FAT: FAT read failed (blocknr 84779)
[35798.912418] FAT: FAT read failed (blocknr 84779)
[35798.912433] FAT: FAT read failed (blocknr 84779)
[35798.912447] FAT: FAT read failed (blocknr 84779)
[35798.912464] FAT: FAT read failed (blocknr 84779)
[35798.912480] FAT: FAT read failed (blocknr 84779)
[35798.912495] FAT: FAT read failed (blocknr 84779)
[35798.912509] FAT: FAT read failed (blocknr 84779)
[35798.912524] FAT: FAT read failed (blocknr 84779)
[35798.912538] FAT: FAT read failed (blocknr 84779)
[35798.912552] FAT: FAT read failed (blocknr 84779)
[35798.912567] FAT: FAT read failed (blocknr 84779)
[35798.912581] FAT: FAT read failed (blocknr 84779)
[35798.912598] FAT: FAT read failed (blocknr 84779)
[35798.912615] FAT: FAT read failed (blocknr 84779)
[35798.912629] FAT: FAT read failed (blocknr 84779)
[35798.912644] FAT: FAT read failed (blocknr 84779)
[35798.912658] FAT: FAT read failed (blocknr 84779)
[35798.912673] FAT: FAT read failed (blocknr 84779)
[35798.912687] FAT: FAT read failed (blocknr 84779)
[35798.912701] FAT: FAT read failed (blocknr 84779)
[35798.912716] FAT: FAT read failed (blocknr 84779)
[35798.912733] FAT: FAT read failed (blocknr 84779)
[35798.912749] FAT: FAT read failed (blocknr 84779)
[35798.912764] FAT: FAT read failed (blocknr 84779)
[35798.912778] FAT: FAT read failed (blocknr 84779)
[35798.912793] FAT: FAT read failed (blocknr 84779)
[35798.912807] FAT: FAT read failed (blocknr 84779)
[35798.912822] FAT: FAT read failed (blocknr 84779)
[35798.912836] FAT: FAT read failed (blocknr 84779)
[35798.912851] FAT: FAT read failed (blocknr 84779)
[35798.912868] FAT: FAT read failed (blocknr 84779)
[35798.912894] FAT: FAT read failed (blocknr 84779)
[35798.912909] FAT: FAT read failed (blocknr 84779)
[35798.912924] FAT: FAT read failed (blocknr 84779)
[35798.912940] FAT: FAT read failed (blocknr 84779)
[35798.912954] FAT: FAT read failed (blocknr 84779)
[35798.912969] FAT: FAT read failed (blocknr 84779)
[35798.912983] FAT: FAT read failed (blocknr 84779)
[35798.914625] FAT: FAT read failed (blocknr 84779)
[35798.914694] FAT: FAT read failed (blocknr 84779)
[35798.914725] FAT: FAT read failed (blocknr 84779)
[35798.914752] FAT: FAT read failed (blocknr 84779)
[35798.914778] FAT: FAT read failed (blocknr 84779)
[35798.914805] FAT: FAT read failed (blocknr 84779)
[35798.914832] FAT: FAT read failed (blocknr 84779)
[35798.914859] FAT: FAT read failed (blocknr 84779)
[35798.914885] FAT: FAT read failed (blocknr 84779)
[35798.914911] FAT: FAT read failed (blocknr 84779)
[35798.914942] FAT: FAT read failed (blocknr 84779)
[35798.914969] FAT: FAT read failed (blocknr 84779)
[35798.914996] FAT: FAT read failed (blocknr 84779)
[35798.915022] FAT: FAT read failed (blocknr 84779)
[35798.915048] FAT: FAT read failed (blocknr 84779)
[35798.915074] FAT: FAT read failed (blocknr 84779)
[35798.915101] FAT: FAT read failed (blocknr 84779)
[35798.915127] FAT: FAT read failed (blocknr 84779)
[35798.918217] FAT: Directory bread(block 34669432) failed
[35798.918248] FAT: Directory bread(block 34669433) failed
[35798.918277] FAT: Directory bread(block 34669434) failed
[35798.918304] FAT: Directory bread(block 34669435) failed
[35798.918332] FAT: Directory bread(block 34669436) failed
[35798.918359] FAT: Directory bread(block 34669437) failed
[35798.918387] FAT: Directory bread(block 34669438) failed
[35798.918414] FAT: Directory bread(block 34669439) failed
[35798.918442] FAT: Directory bread(block 34669440) failed
[35798.918470] FAT: Directory bread(block 34669441) failed
[35798.918497] FAT: Directory bread(block 34669442) failed
[35798.918525] FAT: Directory bread(block 34669443) failed
[35798.918552] FAT: Directory bread(block 34669444) failed
[35798.918580] FAT: Directory bread(block 34669445) failed
[35798.918608] FAT: Directory bread(block 34669446) failed
[35798.918636] FAT: Directory bread(block 34669447) failed
[35798.918663] FAT: Directory bread(block 34669448) failed
[35798.918691] FAT: Directory bread(block 34669449) failed
[35798.918718] FAT: Directory bread(block 34669450) failed
[35798.918746] FAT: Directory bread(block 34669451) failed
[35798.918773] FAT: Directory bread(block 34669452) failed
[35798.918800] FAT: Directory bread(block 34669453) failed
[35798.918828] FAT: Directory bread(block 34669454) failed
[35798.918856] FAT: Directory bread(block 34669455) failed
[35798.918883] FAT: Directory bread(block 34669456) failed
[35798.918911] FAT: Directory bread(block 34669457) failed
[35798.918938] FAT: Directory bread(block 34669458) failed
[35798.918966] FAT: Directory bread(block 34669459) failed
[35798.918993] FAT: Directory bread(block 34669460) failed
[35798.919021] FAT: Directory bread(block 34669461) failed
[35798.919048] FAT: Directory bread(block 34669462) failed
[35798.919075] FAT: Directory bread(block 34669463) failed
[35798.919103] FAT: Directory bread(block 34669464) failed
[35798.919132] FAT: Directory bread(block 34669465) failed
[35798.919160] FAT: Directory bread(block 34669466) failed
[35798.919187] FAT: Directory bread(block 34669467) failed
[35798.919215] FAT: Directory bread(block 34669468) failed
[35798.919243] FAT: Directory bread(block 34669469) failed
[35798.919271] FAT: Directory bread(block 34669470) failed
[35798.919298] FAT: Directory bread(block 34669471) failed
[35798.919326] FAT: Directory bread(block 34669472) failed
[35798.919354] FAT: Directory bread(block 34669473) failed
[35798.919381] FAT: Directory bread(block 34669474) failed
[35798.919408] FAT: Directory bread(block 34669475) failed
[35798.919436] FAT: Directory bread(block 34669476) failed
[35798.919464] FAT: Directory bread(block 34669477) failed
[35798.919491] FAT: Directory bread(block 34669478) failed
[35798.919518] FAT: Directory bread(block 34669479) failed
[35798.919546] FAT: Directory bread(block 34669480) failed
[35798.919573] FAT: Directory bread(block 34669481) failed
[35798.919602] FAT: Directory bread(block 34669482) failed
[35798.919629] FAT: Directory bread(block 34669483) failed
[35798.919658] FAT: Directory bread(block 34669484) failed
[35798.919686] FAT: Directory bread(block 34669485) failed
[35798.919713] FAT: Directory bread(block 34669486) failed
[35798.919741] FAT: Directory bread(block 34669487) failed
[35798.919768] FAT: Directory bread(block 34669488) failed
[35798.919796] FAT: Directory bread(block 34669489) failed
[35798.919823] FAT: Directory bread(block 34669490) failed
[35798.919851] FAT: Directory bread(block 34669491) failed
[35798.919878] FAT: Directory bread(block 34669492) failed
[35798.919906] FAT: Directory bread(block 34669493) failed
[35798.919933] FAT: Directory bread(block 34669494) failed
[35798.919961] FAT: Directory bread(block 34669495) failed
[35798.925079] __ratelimit: 1606 callbacks suppressed
[35798.925090] Buffer I/O error on device sdc1, logical block 679839291
[35798.925101] lost page write due to I/O error on sdc1
[35798.925170] FAT: unable to read inode block for updating (i_pos 10877428669)
[35799.369052] usb 7-4: new high speed USB device using ehci_hcd and address 17
[35799.501837] usb 7-4: configuration #1 chosen from 1 choice
[35799.503304] scsi19 : SCSI emulation for USB Mass Storage devices
[35799.506078] usb-storage: device found at 17
[35799.506090] usb-storage: waiting for device to settle before scanning
[35804.504438] usb-storage: device scan complete
[35804.506672] scsi 19:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[35804.510232] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.510759] sd 19:0:0:0: [sdb] Write Protect is off
[35804.510771] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.510779] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511470] sd 19:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[35804.511967] sd 19:0:0:0: [sdb] Write Protect is off
[35804.511976] sd 19:0:0:0: [sdb] Mode Sense: 23 00 00 00
[35804.511984] sd 19:0:0:0: [sdb] Assuming drive cache: write through
[35804.511997]  sdb: sdb1
[35804.540663] sd 19:0:0:0: [sdb] Attached SCSI disk
[35804.540881] sd 19:0:0:0: Attached scsi generic sg2 type 0
[35816.546231] ath5k phy0: unsupported jumbo
[36066.307003] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=83.157.171.11 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=108 ID=29854 PROTO=UDP SPT=55934 DPT=49786 LEN=111 
[36158.000087] CE: hpet increasing min_delta_ns to 15000 nsec
[36289.192131] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=91.153.200.10 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=113 ID=7426 PROTO=UDP SPT=63639 DPT=49786 LEN=111 
[36291.182588] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=119.246.78.87 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=47 ID=5255 PROTO=UDP SPT=12764 DPT=49786 LEN=111 
[36313.756970] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=203.218.223.100 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=114 ID=15391 PROTO=UDP SPT=19107 DPT=49786 LEN=55 
[36318.475670] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=123.139.61.159 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=110 ID=31171 PROTO=UDP SPT=21075 DPT=49786 LEN=55 
[36333.147312] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=71.103.49.170 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=110 ID=12307 PROTO=UDP SPT=50460 DPT=49786 LEN=111 
[36340.646009] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=97.85.176.56 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=112 ID=13387 PROTO=UDP SPT=20266 DPT=49786 LEN=55 
[36352.909419] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=220.136.47.196 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=105 ID=2414 PROTO=UDP SPT=20935 DPT=49786 LEN=55 
[36363.078463] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=62.43.68.145 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=110 ID=11795 PROTO=UDP SPT=13110 DPT=49786 LEN=55 
[36370.250832] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=200.104.49.33 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=117 ID=24672 PROTO=UDP SPT=21502 DPT=49786 LEN=274 
[36371.336018] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=122.123.0.112 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=105 ID=60581 PROTO=UDP SPT=25980 DPT=49786 LEN=55 
[36388.728427] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=85.229.184.249 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=104 ID=19849 PROTO=UDP SPT=17746 DPT=49786 LEN=274 
[36396.758575] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=24.207.140.186 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=112 ID=7417 PROTO=UDP SPT=20794 DPT=49786 LEN=55 
[36417.040679] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=58.252.51.84 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=111 ID=11352 PROTO=UDP SPT=59217 DPT=49786 LEN=274 
[36438.476937] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=221.0.104.129 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=47 ID=8302 PROTO=UDP SPT=26570 DPT=49786 LEN=55 
[36460.016634] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=71.68.223.237 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=115 ID=3595 PROTO=UDP SPT=11874 DPT=49786 LEN=55 
[36495.805511] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=118.160.232.222 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=106 ID=37112 PROTO=UDP SPT=20846 DPT=49786 LEN=274 
[36529.355859] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=222.150.45.179 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=106 ID=28092 PROTO=UDP SPT=20466 DPT=49786 LEN=55 
[36536.244482] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=83.7.189.167 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=111 ID=13434 PROTO=UDP SPT=18071 DPT=49786 LEN=274 
[36536.984805] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=201.92.37.200 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=108 ID=62278 PROTO=UDP SPT=59367 DPT=49786 LEN=55 
[36577.323643] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=61.62.95.174 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=113 ID=19467 PROTO=UDP SPT=12204 DPT=49786 LEN=274 
[36587.214080] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=79.114.218.188 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=109 ID=11529 PROTO=UDP SPT=21268 DPT=49786 LEN=55 
[36596.148606] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=219.211.238.178 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=107 ID=19932 PROTO=UDP SPT=40970 DPT=49786 LEN=111 
[36601.699723] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=76.65.19.44 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=115 ID=7664 PROTO=UDP SPT=23325 DPT=49786 LEN=55 
[36610.393726] ath5k phy0: unsupported jumbo
[36611.866877] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=122.133.47.197 DST=192.168.2.21 LEN=75 TOS=0x00 PREC=0x20 TTL=107 ID=20849 PROTO=UDP SPT=22926 DPT=49786 LEN=55 
[36626.610609] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=70.81.209.50 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=109 ID=39827 PROTO=UDP SPT=14504 DPT=49786 LEN=274 
[36651.751753] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=88.195.69.184 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=110 ID=54883 PROTO=UDP SPT=21557 DPT=49786 LEN=274 
[36678.800488] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=125.224.119.145 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=105 ID=43960 PROTO=UDP SPT=8419 DPT=49786 LEN=274 
[36721.396878] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=64.17.89.10 DST=192.168.2.21 LEN=294 TOS=0x00 PREC=0x20 TTL=110 ID=57658 PROTO=UDP SPT=41445 DPT=49786 LEN=274 
[36721.460434] ehci_hcd 0000:00:1d.7: remove, state 1
[36721.461430] usb usb7: USB disconnect, address 1
[36721.461440] usb 7-4: USB disconnect, address 17
[36721.475687] ehci_hcd 0000:00:1d.7: USB bus 7 deregistered
[36721.476880] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[36721.477883] ehci_hcd 0000:00:1a.7: remove, state 4
[36721.478791] usb usb3: USB disconnect, address 1
[36721.484002] ehci_hcd 0000:00:1a.7: USB bus 3 deregistered
[36721.484361] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[36721.776044] usb 5-2: new full speed USB device using uhci_hcd and address 4
[36721.938359] usb 5-2: configuration #1 chosen from 1 choice
[36721.946118] scsi20 : SCSI emulation for USB Mass Storage devices
[36721.946676] usb-storage: device found at 4
[36721.946680] usb-storage: waiting for device to settle before scanning
[36726.953079] usb-storage: device scan complete
[36726.956236] scsi 20:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[36726.969127] sd 20:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[36726.975381] sd 20:0:0:0: [sdb] Write Protect is off
[36726.975397] sd 20:0:0:0: [sdb] Mode Sense: 23 00 00 00
[36726.975404] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[36726.981215] sd 20:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[36726.985230] sd 20:0:0:0: [sdb] Write Protect is off
[36726.985246] sd 20:0:0:0: [sdb] Mode Sense: 23 00 00 00
[36726.985253] sd 20:0:0:0: [sdb] Assuming drive cache: write through
[36726.985267]  sdb: sdb1
[36734.327601] sd 20:0:0:0: [sdb] Attached SCSI disk
[36734.327844] sd 20:0:0:0: Attached scsi generic sg2 type 0
[36802.171673] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=116.232.204.183 DST=192.168.2.21 LEN=126 TOS=0x00 PREC=0x20 TTL=112 ID=64418 PROTO=UDP SPT=18980 DPT=49786 LEN=106 
[36816.203075] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=118.173.67.27 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=94 ID=42853 PROTO=UDP SPT=8231 DPT=49786 LEN=111 
[36830.940052] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=190.58.69.237 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=111 ID=30154 PROTO=UDP SPT=28538 DPT=49786 LEN=111 
[36835.688831] ath5k phy0: unsupported jumbo
[36838.241893] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=152.7.16.122 DST=192.168.2.21 LEN=95 TOS=0x00 PREC=0x20 TTL=110 ID=26947 PROTO=UDP SPT=27289 DPT=49786 LEN=75 
[36927.198765] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=118.101.105.132 DST=192.168.2.21 LEN=129 TOS=0x00 PREC=0x20 TTL=106 ID=31894 PROTO=UDP SPT=6881 DPT=49786 LEN=109 
[37025.014542] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=81.220.96.111 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=44 ID=16374 PROTO=UDP SPT=20200 DPT=49786 LEN=111 
[37028.411825] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=81.220.96.111 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=44 ID=16774 PROTO=UDP SPT=20200 DPT=49786 LEN=111 
[37029.450739] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=81.220.96.111 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=44 ID=16909 PROTO=UDP SPT=20200 DPT=49786 LEN=111 
[37034.390522] [UFW ALLOW INPUT]: IN=wlan1 OUT= MAC=00:1d:d9:78:29:8a:00:1c:df:d7:ba:af:08:00 SRC=84.27.58.206 DST=192.168.2.21 LEN=131 TOS=0x00 PREC=0x20 TTL=106 ID=61486 PROTO=UDP SPT=7000 DPT=49786 LEN=111 
[37074.373924] ath5k phy0: unsupported jumbo
[37372.319981] loop: module loaded
[37718.239788] ath5k phy0: unsupported jumbo
[37965.277204] CPU0 attaching NULL sched-domain.
[37965.277226] CPU1 attaching NULL sched-domain.
[37965.316413] CPU0 attaching sched-domain:
[37965.316426]  domain 0: span 0-1 level MC
[37965.316434]   groups: 0 1
[37965.316448] CPU1 attaching sched-domain:
[37965.316454]  domain 0: span 0-1 level MC
[37965.316459]   groups: 1 0

```




Now, formatting would be something that I reallllly... don't want to do.


It's a 1tb 

it came as fat32


I have about 150 gigs so far on it.

but i mean, if i have to....

---

### Post by Rocket2DMn on 2009-04-25
Ok, well I'm not seeing that error appear anymore after we disabled the ehci_hcd module.  Are you able to write to the disk OK now?  I expect transfer would be slow, but if it works, we can make the leap and say that the problem was with the ehci_hcd module, and then you can file a bug report.  I would be happy to help you with this as well.

---

### Post by qjmoss on 2009-04-25
My torrents seem to be stable.

is there a fix to this, i would like to have the top speed for transfers ; )

But yes, if you would like to help with reporting the bug, that would be nice =)

---

### Post by Rocket2DMn on 2009-04-25
That module is needed for hi speed USB transfers, I don't have a workaround for you.
I have a [guide that you can follow]("http://ubuntuforums.org/showthread.php?t=1011078") to file a bug report; the link is also in my signature.  You will want to file a bug against the package "linux" which is for the kernel (which includes that module).  If you have any questions about the guide, please feel free to ask, and after you report the bug, post a link here.

---

### Post by qjmoss on 2009-04-25
That bug seems to be reported many times.


One more question..


Do you think, if i were to update to 9.04, my wireless card would work.

It took me a lot of sanity to get my card to work, and i dont want to have to start over.


Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

is it supported in the update?

---

### Post by Rocket2DMn on 2009-04-25
Based on a quick search of bugs, it sounds like Atheros cards still have a fair number of problems.  You will need to start a separate thread for that issue, I don't know much about configuring wireless cards and dealing with Atheros drivers.

---

### Post by qjmoss on 2009-04-25
okay, well i figured... but now i'm getting Invalid argument as an error

---

### Post by Rocket2DMn on 2009-04-25
Ok, why don't you go ahead and file that bug report then and post a link here.  You can also run fsck on the partition to see if anything is found.  Make sure the drive is plugged in, but unmounted, and run
```
sudo fsck /dev/sdb1
```
and see if anything shows up (it could take awhile to run).

I'm afraid I don't know how else to proceed without reformatting the drive with a fresh FAT32 partition or trying another filesystem type.  Sorry.

---

### Post by qjmoss on 2009-04-25
Okay, well I guess we can just format it =(

Whats the best way to go about this, with a new filesystem type that wont put me through this again.

---

### Post by Rocket2DMn on 2009-04-25
If you will be sharing this drive with a Windows operating system at all, I would just go ahead and use NTFS.  If you think you will only use the drive with Ubuntu, I would format it as ext3.  The easiest way is to install the package gparted and format it from directly in Ubuntu rather than using a livecd.
```
sudo apt-get install gparted
```
Then to open GParted, go to System->Administration->Partition Editor, select /dev/sdb from the top right and go for it.  The procedure should be pretty straightforward - you will delete the existing partitions and format the entire drive with one new parition of the correct filesystem.

Of course, back up everything off the drive beforehand if you need to since all data on it will be wiped.

---

### Post by qjmoss on 2009-04-26
I've been watching the errors and seeing when they appear.   and it seems, that when I have a large file downloading.. it will error.  I have one torrent that is one gig. and another that is 7 gigs, and the 7 gig fails repeatedly.

If that is any help to anyone...

---

### Post by Rocket2DMn on 2009-04-26
The maximum size of a file that you can fit on a FAT32 partition is 4GB.  Any single file larger than that will fail, it is a limitation of the filesystem.  If you want files larger, you need another option, like NTFS (windows compatible) or ext3 (a linux filesystem, not natively windows compatible).

---

### Post by qjmoss on 2009-04-26
So am I going to have to reformat the whole drive =(

---

### Post by Rocket2DMn on 2009-04-26
If you want to hold files larger than 4GB, yes.  Do you have a means to backup the existing contents of the drive beforehand?

---

### Post by qjmoss on 2009-04-27
Well, what I did was take everything from my external and put it on my laptop harddrive. and i'm going to put it back on my external when i'm done formatting.

I've run into one more problem, when i go to format, I can only format to ext3

no other choices.

=/

but i would like to use my external with my windows pc too..

---

### Post by qjmoss on 2009-04-27
I get an error when trying to format



```
GParted 0.3.8

Libparted 1.8.9

Format /dev/sdb1 as ext3  00:05:10    ( ERROR )
     	
calibrate /dev/sdb1  00:00:01    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 1953520064
size: 1953520002 (931.51 GiB)
set partitiontype on /dev/sdb1  00:00:00    ( SUCCESS )
     	
new partitiontype: ext3
create new ext3 filesystem  00:05:09    ( ERROR )
     	
mkfs.ext3 -L "" /dev/sdb1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
61054976 inodes, 244190000 blocks
12209500 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
7453 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000, 214990848

Writing inode tables: 0/7453 1/7453 2/7453 3/7453 4/7453 5/7453 6/7453 7/7453 8/7453 9/7453 10/7453 11/7453 12/7453 13/7453 14/7453 15/7453 16/7453 17/7453 18/7453 19/7453 20/7453 21/7453 22/7453 23/7453 24/7453 25/7453 26/7453 27/7453 28/7453 29/7453 30/7453 31/7453 32/7453 33/7453 34/7453 35/7453 36/7453 37/7453 38/7453 39/7453 40/7453 41/7453 42/7453 43/7453 44/7453 45/7453 46/7453 47/7453 48/7453 49/7453 50/7453 51/7453 52/7453 53/7453 54/7453 55/7453 56/7453 57/7453 58/7453 59/7453 60/7453 61/7453 62/7453 63/7453 64/7453 65/7453 66/7453 67/7453 68/7453 69/7453 70/7453 71/7453 72/7453 73/7453 74/7453 75/7453 76/7453 77/7453 78/7453 79/7453 80/7453 81/7453 82/7453 83/7453 84/7453 85/7453 86/7453 87/7453 88/7453 89/7453 90/7453 91/7453 92/7453 93/7453 94/7453 95/7453 96/7453 97/7453 98/7453 99/7453 100/7453 101/7453 102/7453 103/7453 104/7453 105/7453 106/7453 107/7453 108/7453 109/7453 110/7453 111/7453 112/7453 113/7453 114/7453 115/7453 116/7453 117/7453 118/7453 119/7453 120/7453 121/7453 122/7453 123/7453 124/7453 125/7453 126/7453 127/7453 128/7453 129/7453 130/7453 131/7453 132/7453 133/7453 134/7453 135/7453 136/7453 137/7453 138/7453 139/7453 140/7453 141/7453 142/7453 143/7453 144/7453 145/7453 146/7453 147/7453 148/7453 149/7453 150/7453 151/7453 152/7453 153/7453 154/7453 155/7453 156/7453 157/7453 158/7453 159/7453 160/7453 161/7453 162/7453 163/7453 164/7453 165/7453 166/7453 167/7453 168/7453 169/7453 170/7453 171/7453 172/7453 173/7453 174/7453 175/7453 176/7453 177/7453 178/7453 179/7453 180/7453 181/7453 182/7453 183/7453 184/7453 185/7453 186/7453 187/7453 188/7453 189/7453 190/7453 191/7453 192/7453 193/7453 194/7453 195/7453 196/7453 197/7453 198/7453 199/7453 200/7453 201/7453 202/7453 203/7453 204/7453 205/7453 206/7453 207/7453 208/7453 209/7453 210/7453 211/7453 212/7453 213/7453 214/7453 215/7453 216/7453 217/7453 218/7453 219/7453 220/7453 221/7453 222/7453 223/7453 224/7453 225/7453 226/7453 227/7453 228/7453 229/7453 230/7453 231/7453 232/7453 233/7453 234/7453 235/7453 236/7453 237/7453 238/7453 239/7453 240/7453 241/7453 242/7453 243/7453 244/7453 245/7453 246/7453 247/7453 248/7453 249/7453 250/7453 251/7453 252/7453 253/7453 254/7453 255/7453 256/7453 257/7453 258/7453 259/7453 260/7453 261/7453 262/7453 263/7453 264/7453 265/7453 266/7453 267/7453 268/7453 269/7453 270/7453 271/7453 272/7453 273/7453 274/7453 275/7453 276/7453 277/7453 278/7453 279/7453 280/7453 281/7453 282/7453 283/7453 284/7453 285/7453 286/7453 287/7453 288/7453 289/7453 290/7453 291/7453 292/7453 293/7453 294/7453 295/7453 296/7453 297/7453 298/7453 299/7453 300/7453 301/7453 302/7453 303/7453 304/7453 305/7453 306/7453 307/7453 308/7453 309/7453 310/7453 311/7453 312/7453 313/7453 314/7453 315/7453 316/7453 317/7453 318/7453 319/7453 320/7453 321/7453 322/7453 323/7453 324/7453 325/7453 326/7453 327/7453 328/7453 329/7453 330/7453 331/7453 332/7453 333/7453 334/7453 335/7453 336/7453 337/7453 338/7453 339/7453 340/7453 341/7453 342/7453 343/7453 344/7453 345/7453 346/7453 347/7453 348/7453 349/7453 350/7453 351/7453 352/7453 353/7453 354/7453 355/7453 356/7453 357/7453 358/7453 359/7453 360/7453 361/7453 362/7453 363/7453 364/7453 365/7453 366/7453 367/7453 368/7453 369/7453 370/7453 371/7453 372/7453 373/7453 374/7453 375/7453 376/7453 377/7453 378/7453 379/7453 380/7453 381/7453 382/7453 383/7453 384/7453 385/7453 386/7453 387/7453 388/7453 389/7453 390/7453 391/7453 392/7453 393/7453 394/7453 395/7453 396/7453 397/7453 398/7453 399/7453 400/7453 401/7453 402/7453 403/7453 404/7453 405/7453 406/7453 407/7453 408/7453 409/7453 410/7453 411/7453 412/7453 413/7453 414/7453 415/7453 416/7453 417/7453 418/7453 419/7453 420/7453 421/7453 422/7453 423/7453 424/7453 425/7453 426/7453 427/7453 428/7453 429/7453 430/7453 431/7453 432/7453 433/7453 434/7453 435/7453 436/7453 437/7453 438/7453 439/7453 440/7453 441/7453 442/7453 443/7453 444/7453 445/7453 446/7453 447/7453 448/7453 449/7453 450/7453 451/7453 452/7453 453/7453 454/7453 455/7453 456/7453 457/7453 458/7453 459/7453 460/7453 461/7453 462/7453 463/7453 464/7453 465/7453 466/7453 467/7453 468/7453 469/7453 470/7453 471/7453 472/7453 473/7453 474/7453 475/7453 476/7453 477/7453 478/7453 479/7453 480/7453 481/7453 482/7453 483/7453 484/7453 485/7453 486/7453 487/7453 488/7453 489/7453 490/7453 491/7453 492/7453 493/7453 494/7453 495/7453 496/7453 497/7453 498/7453 499/7453 500/7453 501/7453 502/7453 503/7453 504/7453 505/7453 506/7453 507/7453 508/7453 509/7453 510/7453 511/7453 512/7453 513/7453 514/7453 515/7453 516/7453 517/7453 518/7453 519/7453 520/7453 521/7453 522/7453 523/7453 524/7453 525/7453 526/7453 527/7453 528/7453 529/7453 530/7453 531/7453 532/7453 533/7453 534/7453 535/7453 536/7453 537/7453 538/7453 539/7453 540/7453 541/7453 542/7453 543/7453 544/7453 545/7453 546/7453 547/7453 548/7453 549/7453 550/7453 551/7453 552/7453 553/7453 554/7453 555/7453 556/7453 557/7453 558/7453 559/7453 560/7453 561/7453 562/7453 563/7453 564/7453 565/7453 566/7453 567/7453 568/7453 569/7453 570/7453 571/7453 572/7453 573/7453 574/7453 575/7453 576/7453 577/7453 578/7453 579/7453 580/7453 581/7453 582/7453 583/7453 584/7453 585/7453 586/7453 587/7453 588/7453 589/7453 590/7453 591/7453 592/7453 593/7453 594/7453 595/7453 596/7453 597/7453 598/7453 599/7453 600/7453 601/7453 602/7453 603/7453 604/7453 605/7453 606/7453 607/7453 608/7453 609/7453 610/7453 611/7453 612/7453 613/7453 614/7453 615/7453 616/7453 617/7453 618/7453 619/7453 620/7453 621/7453 622/7453 623/7453 624/7453 625/7453 626/7453 627/7453 628/7453 629/7453 630/7453 631/7453 632/7453 633/7453 634/7453 635/7453 636/7453 637/7453 638/7453 639/7453 640/7453 641/7453 642/7453 643/7453 644/7453 645/7453 646/7453 647/7453 648/7453 649/7453 650/7453 651/7453 652/7453 653/7453 654/7453 655/7453 656/7453 657/7453 658/7453 659/7453 660/7453 661/7453 662/7453 663/7453 664/7453 665/7453 666/7453 667/7453 668/7453 669/7453 670/7453 671/7453 672/7453 673/7453 674/7453 675/7453 676/7453 677/7453 678/7453 679/7453 680/7453 681/7453 682/7453 683/7453 684/7453 685/7453 686/7453 687/7453 688/7453 689/7453 690/7453 691/7453 692/7453 693/7453 694/7453 695/7453 696/7453 697/7453 698/7453 699/7453 700/7453 701/7453 702/7453 703/7453 704/7453 705/7453 706/7453 707/7453 708/7453 709/7453 710/7453 711/7453 712/7453 713/7453 714/7453 715/7453 716/7453 717/7453 718/7453 719/7453 720/7453 721/7453 722/7453 723/7453 724/7453 725/7453 726/7453 727/7453 728/7453 729/7453 730/7453 731/7453 732/7453 733/7453 734/7453 735/7453 736/7453 737/7453 738/7453 739/7453 740/7453 741/7453 742/7453 743/7453 744/7453 745/7453 746/7453 747/7453 748/7453 749/7453 750/7453 751/7453 752/7453 753/7453 754/7453 755/7453 756/7453 757/7453 758/7453 759/7453 760/7453 761/7453 762/7453 763/7453 764/7453 765/7453 766/7453 767/7453 768/7453 769/7453 770/7453 771/7453 772/7453 773/7453 774/7453 775/7453 776/7453 777/7453 778/7453 779/7453 780/7453 781/7453 782/7453 783/7453 784/7453 785/7453 786/7453 787/7453 788/7453 789/7453 790/7453 791/7453 792/7453 793/7453 794/7453 795/7453 796/7453 797/7453 798/7453 799/7453 800/7453 801/7453 802/7453 803/7453 804/7453 805/7453 806/7453 807/7453 808/7453 809/7453 810/7453 811/7453 812/7453 813/7453 814/7453 815/7453 816/7453 817/7453 818/7453 819/7453 820/7453 821/7453 822/7453 823/7453 824/7453 825/7453 826/7453 827/7453 828/7453 829/7453 830/7453 831/7453 832/7453 833/7453 834/7453 835/7453 836/7453 837/7453 838/7453 839/7453 840/7453 841/7453 842/7453 843/7453 844/7453 845/7453 846/7453 847/7453 848/7453 849/7453 850/7453 851/7453 852/7453 853/7453 854/7453 855/7453 856/7453 857/7453 858/7453 859/7453 860/7453 861/7453 862/7453 863/7453 864/7453 865/7453 866/7453 867/7453 868/7453 869/7453 870/7453 871/7453 872/7453 873/7453 874/7453 875/7453 876/7453 877/7453 878/7453 879/7453 880/7453 881/7453 882/7453 883/7453 884/7453 885/7453 886/7453 887/7453 888/7453 889/7453 890/7453 891/7453 892/7453 893/7453 894/7453 895/7453 896/7453 897/7453 898/7453 899/7453 900/7453 901/7453 902/7453 903/7453 904/7453 905/7453 906/7453 907/7453 908/7453 909/7453 910/7453 911/7453 912/7453 913/7453 914/7453 915/7453 916/7453 917/7453 918/7453 919/7453 920/7453 921/7453 922/7453 923/7453 924/7453 925/7453 926/7453 927/7453 928/7453 929/7453 930/7453 931/7453 932/7453 933/7453 934/7453 935/7453 936/7453 937/7453 938/7453 939/7453 940/7453 941/7453 942/7453 943/7453 944/7453 945/7453 946/7453 947/7453 948/7453 949/7453 950/7453 951/7453 952/7453 953/7453 954/7453 955/7453 956/7453 957/7453 958/7453 959/7453 960/7453 961/7453 962/7453 963/7453 964/7453 965/7453 966/7453 967/7453 968/7453 969/7453 970/7453 971/7453 972/7453 973/7453 974/7453 975/7453 976/7453 977/7453 978/7453 979/7453 980/7453 981/7453 982/7453 983/7453 984/7453 985/7453 986/7453 987/7453 988/7453 989/7453 990/7453 991/7453 992/7453 993/7453 994/7453 995/7453 996/7453 997/7453 998/7453 999/74531000/74531001/74531002/74531003/74531004/74531005/74531006/74531007/74531008/74531009/74531010/74531011/74531012/74531013/74531014/74531015/74531016/74531017/74531018/74531019/74531020/74531021/74531022/74531023/74531024/74531025/74531026/74531027/74531028/74531029/74531030/74531031/74531032/74531033/74531034/74531035/74531036/74531037/74531038/74531039/74531040/74531041/74531042/74531043/74531044/74531045/74531046/74531047/74531048/74531049/74531050/74531051/74531052/74531053/74531054/74531055/74531056/74531057/74531058/74531059/74531060/74531061/74531062/74531063/74531064/74531065/74531066/74531067/74531068/74531069/74531070/74531071/74531072/74531073/74531074/74531075/74531076/74531077/74531078/74531079/74531080/74531081/74531082/74531083/74531084/74531085/74531086/74531087/74531088/74531089/74531090/74531091/74531092/74531093/74531094/74531095/74531096/74531097/74531098/74531099/74531100/74531101/74531102/74531103/74531104/74531105/74531106/74531107/74531108/74531109/74531110/74531111/74531112/74531113/74531114/74531115/74531116/74531117/74531118/74531119/74531120/74531121/74531122/74531123/74531124/74531125/74531126/74531127/74531128/74531129/74531130/74531131/74531132/74531133/74531134/74531135/74531136/74531137/74531138/74531139/74531140/74531141/74531142/74531143/74531144/74531145/74531146/74531147/74531148/74531149/74531150/74531151/74531152/74531153/74531154/74531155/74531156/74531157/74531158/74531159/74531160/74531161/74531162/74531163/74531164/74531165/74531166/74531167/74531168/74531169/74531170/74531171/74531172/74531173/74531174/74531175/74531176/74531177/74531178/74531179/74531180/74531181/74531182/74531183/74531184/74531185/74531186/74531187/74531188/74531189/74531190/74531191/74531192/74531193/74531194/74531195/74531196/74531197/74531198/74531199/74531200/74531201/74531202/74531203/74531204/74531205/74531206/74531207/74531208/74531209/74531210/74531211/74531212/74531213/74531214/74531215/74531216/74531217/74531218/74531219/74531220/74531221/74531222/74531223/74531224/74531225/74531226/74531227/74531228/74531229/74531230/74531231/74531232/74531233/74531234/74531235/74531236/74531237/74531238/74531239/74531240/74531241/74531242/74531243/74531244/74531245/74531246/74531247/74531248/74531249/74531250/74531251/74531252/74531253/74531254/74531255/74531256/74531257/74531258/74531259/74531260/74531261/74531262/74531263/74531264/74531265/74531266/74531267/74531268/74531269/74531270/74531271/74531272/74531273/74531274/74531275/74531276/74531277/74531278/74531279/74531280/74531281/74531282/74531283/74531284/74531285/74531286/74531287/74531288/74531289/74531290/74531291/74531292/74531293/74531294/74531295/74531296/74531297/74531298/74531299/74531300/74531301/74531302/74531303/74531304/74531305/74531306/74531307/74531308/74531309/74531310/74531311/74531312/74531313/74531314/74531315/74531316/74531317/74531318/74531319/74531320/74531321/74531322/74531323/74531324/74531325/74531326/74531327/74531328/74531329/74531330/74531331/74531332/74531333/74531334/74531335/74531336/74531337/74531338/74531339/74531340/74531341/74531342/74531343/74531344/74531345/74531346/74531347/74531348/74531349/74531350/74531351/74531352/74531353/74531354/74531355/74531356/74531357/74531358/74531359/74531360/74531361/74531362/74531363/74531364/74531365/74531366/74531367/74531368/74531369/74531370/74531371/74531372/74531373/74531374/74531375/74531376/74531377/74531378/74531379/74531380/74531381/74531382/74531383/74531384/74531385/74531386/74531387/74531388/74531389/74531390/74531391/74531392/74531393/74531394/74531395/74531396/74531397/74531398/74531399/74531400/74531401/74531402/74531403/74531404/74531405/74531406/74531407/74531408/74531409/74531410/74531411/74531412/74531413/74531414/74531415/74531416/74531417/74531418/74531419/74531420/74531421/74531422/74531423/74531424/74531425/74531426/74531427/74531428/74531429/74531430/74531431/74531432/74531433/74531434/74531435/74531436/74531437/74531438/74531439/74531440/74531441/74531442/74531443/74531444/74531445/74531446/74531447/74531448/74531449/74531450/74531451/74531452/74531453/74531454/74531455/74531456/74531457/74531458/74531459/74531460/74531461/74531462/74531463/74531464/74531465/74531466/74531467/74531468/74531469/74531470/74531471/74531472/74531473/74531474/74531475/74531476/74531477/74531478/74531479/74531480/74531481/74531482/74531483/74531484/74531485/74531486/74531487/74531488/74531489/74531490/74531491/74531492/74531493/74531494/74531495/74531496/74531497/74531498/74531499/74531500/74531501/74531502/74531503/74531504/74531505/74531506/74531507/74531508/74531509/74531510/74531511/74531512/74531513/74531514/74531515/74531516/74531517/74531518/74531519/74531520/74531521/74531522/74531523/74531524/74531525/74531526/74531527/74531528/74531529/74531530/74531531/74531532/74531533/74531534/74531535/74531536/74531537/74531538/74531539/74531540/74531541/74531542/74531543/74531544/74531545/74531546/74531547/74531548/74531549/74531550/74531551/74531552/74531553/74531554/74531555/74531556/74531557/74531558/74531559/74531560/74531561/74531562/74531563/74531564/74531565/74531566/74531567/74531568/74531569/74531570/74531571/74531572/74531573/74531574/74531575/74531576/74531577/74531578/74531579/74531580/74531581/74531582/74531583/74531584/74531585/74531586/74531587/74531588/74531589/74531590/74531591/74531592/74531593/74531594/74531595/74531596/74531597/74531598/74531599/74531600/74531601/74531602/74531603/74531604/74531605/74531606/74531607/74531608/74531609/74531610/74531611/74531612/74531613/74531614/74531615/74531616/74531617/74531618/74531619/74531620/74531621/74531622/74531623/74531624/74531625/74531626/74531627/74531628/74531629/74531630/74531631/74531632/74531633/74531634/74531635/74531636/74531637/74531638/74531639/74531640/74531641/74531642/74531643/74531644/74531645/74531646/74531647/74531648/74531649/74531650/74531651/74531652/74531653/74531654/74531655/74531656/74531657/74531658/74531659/74531660/74531661/74531662/74531663/74531664/74531665/74531666/74531667/74531668/74531669/74531670/74531671/74531672/74531673/74531674/74531675/74531676/74531677/74531678/74531679/74531680/74531681/74531682/74531683/74531684/74531685/74531686/74531687/74531688/74531689/74531690/74531691/74531692/74531693/74531694/74531695/74531696/74531697/74531698/74531699/74531700/74531701/74531702/74531703/74531704/74531705/74531706/74531707/74531708/74531709/74531710/74531711/74531712/74531713/74531714/74531715/74531716/74531717/74531718/74531719/74531720/74531721/74531722/74531723/74531724/74531725/74531726/74531727/74531728/74531729/74531730/74531731/74531732/74531733/74531734/74531735/74531736/74531737/74531738/74531739/74531740/74531741/74531742/74531743/74531744/74531745/74531746/74531747/74531748/74531749/74531750/74531751/74531752/74531753/74531754/74531755/74531756/74531757/74531758/74531759/74531760/74531761/74531762/74531763/74531764/74531765/74531766/74531767/74531768/74531769/74531770/74531771/74531772/74531773/74531774/74531775/74531776/74531777/74531778/74531779/74531780/74531781/74531782/74531783/74531784/74531785/74531786/74531787/74531788/74531789/74531790/74531791/74531792/74531793/74531794/74531795/74531796/74531797/74531798/74531799/74531800/74531801/74531802/74531803/74531804/74531805/74531806/74531807/74531808/74531809/74531810/74531811/74531812/74531813/74531814/74531815/74531816/74531817/74531818/74531819/74531820/74531821/74531822/74531823/74531824/74531825/74531826/74531827/74531828/74531829/74531830/74531831/74531832/74531833/74531834/74531835/74531836/74531837/74531838/74531839/74531840/74531841/74531842/74531843/74531844/74531845/74531846/74531847/74531848/74531849/74531850/74531851/74531852/74531853/74531854/74531855/74531856/74531857/74531858/74531859/74531860/74531861/74531862/74531863/74531864/74531865/74531866/74531867/74531868/74531869/74531870/74531871/74531872/74531873/74531874/74531875/74531876/74531877/74531878/74531879/74531880/74531881/74531882/74531883/74531884/74531885/74531886/74531887/74531888/74531889/74531890/74531891/74531892/74531893/74531894/74531895/74531896/74531897/74531898/74531899/74531900/74531901/74531902/74531903/74531904/74531905/74531906/74531907/74531908/74531909/74531910/74531911/74531912/74531913/74531914/74531915/74531916/74531917/74531918/74531919/74531920/74531921/74531922/74531923/74531924/74531925/74531926/74531927/74531928/74531929/74531930/74531931/74531932/74531933/74531934/74531935/74531936/74531937/74531938/74531939/74531940/74531941/74531942/74531943/74531944/74531945/74531946/74531947/74531948/74531949/74531950/74531951/74531952/74531953/74531954/74531955/74531956/74531957/74531958/74531959/74531960/74531961/74531962/74531963/74531964/74531965/74531966/74531967/74531968/74531969/74531970/74531971/74531972/74531973/74531974/74531975/74531976/74531977/74531978/74531979/74531980/74531981/74531982/74531983/74531984/74531985/74531986/74531987/74531988/74531989/74531990/74531991/74531992/74531993/74531994/74531995/74531996/74531997/74531998/74531999/74532000/74532001/74532002/74532003/74532004/74532005/74532006/74532007/74532008/74532009/74532010/74532011/74532012/74532013/74532014/74532015/74532016/74532017/74532018/74532019/74532020/74532021/74532022/74532023/74532024/74532025/74532026/74532027/74532028/74532029/74532030/74532031/74532032/74532033/74532034/74532035/74532036/74532037/74532038/74532039/74532040/74532041/74532042/74532043/74532044/74532045/74532046/74532047/74532048/74532049/74532050/74532051/74532052/74532053/74532054/74532055/74532056/74532057/74532058/74532059/74532060/74532061/74532062/74532063/74532064/74532065/74532066/74532067/74532068/74532069/74532070/74532071/74532072/74532073/74532074/74532075/74532076/74532077/74532078/74532079/74532080/74532081/74532082/74532083/74532084/74532085/74532086/74532087/74532088/74532089/74532090/74532091/74532092/74532093/74532094/74532095/74532096/74532097/74532098/74532099/74532100/74532101/74532102/74532103/74532104/74532105/74532106/74532107/74532108/74532109/74532110/74532111/74532112/74532113/74532114/74532115/74532116/74532117/74532118/74532119/74532120/74532121/74532122/74532123/74532124/74532125/74532126/74532127/74532128/74532129/74532130/74532131/74532132/74532133/74532134/74532135/74532136/74532137/74532138/74532139/74532140/74532141/74532142/74532143/74532144/74532145/74532146/74532147/74532148/74532149/74532150/74532151/74532152/74532153/74532154/74532155/74532156/74532157/74532158/74532159/74532160/74532161/74532162/74532163/74532164/74532165/74532166/74532167/74532168/74532169/74532170/74532171/74532172/74532173/74532174/74532175/74532176/74532177/74532178/74532179/74532180/74532181/74532182/74532183/74532184/74532185/74532186/74532187/74532188/74532189/74532190/74532191/74532192/74532193/74532194/74532195/74532196/74532197/74532198/74532199/74532200/74532201/74532202/74532203/74532204/74532205/74532206/74532207/74532208/74532209/74532210/74532211/74532212/74532213/74532214/74532215/74532216/74532217/74532218/74532219/74532220/74532221/74532222/74532223/74532224/74532225/74532226/74532227/74532228/74532229/74532230/74532231/74532232/74532233/74532234/74532235/74532236/74532237/74532238/74532239/74532240/74532241/74532242/74532243/74532244/74532245/74532246/74532247/74532248/74532249/74532250/74532251/74532252/74532253/74532254/74532255/74532256/74532257/74532258/74532259/74532260/74532261/74532262/74532263/74532264/74532265/74532266/74532267/74532268/74532269/74532270/74532271/74532272/74532273/74532274/74532275/74532276/74532277/74532278/74532279/74532280/74532281/74532282/74532283/74532284/74532285/74532286/74532287/74532288/74532289/74532290/74532291/74532292/74532293/74532294/74532295/74532296/74532297/74532298/74532299/74532300/74532301/74532302/74532303/74532304/74532305/74532306/74532307/74532308/74532309/74532310/74532311/74532312/74532313/74532314/74532315/74532316/74532317/74532318/74532319/74532320/74532321/74532322/74532323/74532324/74532325/74532326/74532327/74532328/74532329/74532330/74532331/74532332/74532333/74532334/74532335/74532336/74532337/74532338/74532339/74532340/74532341/74532342/74532343/74532344/74532345/74532346/74532347/74532348/74532349/74532350/74532351/74532352/74532353/74532354/74532355/74532356/74532357/74532358/74532359/74532360/74532361/74532362/74532363/74532364/74532365/74532366/74532367/74532368/74532369/74532370/74532371/74532372/74532373/74532374/74532375/74532376/74532377/74532378/74532379/74532380/74532381/74532382/74532383/74532384/74532385/74532386/74532387/74532388/74532389/74532390/74532391/74532392/74532393/74532394/74532395/74532396/74532397/74532398/74532399/74532400/74532401/74532402/74532403/74532404/74532405/74532406/74532407/74532408/74532409/74532410/74532411/74532412/74532413/74532414/74532415/74532416/74532417/74532418/74532419/74532420/74532421/74532422/74532423/74532424/74532425/74532426/74532427/74532428/74532429/74532430/74532431/74532432/74532433/74532434/74532435/74532436/74532437/74532438/74532439/74532440/74532441/74532442/74532443/74532444/74532445/74532446/74532447/74532448/74532449/74532450/74532451/74532452/74532453/74532454/74532455/74532456/74532457/74532458/74532459/74532460/74532461/74532462/74532463/74532464/74532465/74532466/74532467/74532468/74532469/74532470/74532471/74532472/74532473/74532474/74532475/74532476/74532477/74532478/74532479/74532480/74532481/74532482/74532483/74532484/74532485/74532486/74532487/74532488/74532489/74532490/74532491/74532492/74532493/74532494/74532495/74532496/74532497/74532498/74532499/74532500/74532501/74532502/74532503/74532504/74532505/74532506/74532507/74532508/74532509/74532510/74532511/74532512/74532513/74532514/74532515/74532516/74532517/74532518/74532519/74532520/74532521/74532522/74532523/74532524/74532525/74532526/74532527/74532528/74532529/74532530/74532531/74532532/74532533/74532534/74532535/74532536/74532537/74532538/74532539/74532540/74532541/74532542/74532543/74532544/74532545/74532546/74532547/74532548/74532549/74532550/74532551/74532552/74532553/74532554/74532555/74532556/74532557/74532558/74532559/74532560/74532561/74532562/74532563/74532564/74532565/74532566/74532567/74532568/74532569/74532570/74532571/74532572/74532573/74532574/74532575/74532576/74532577/74532578/74532579/74532580/74532581/74532582/74532583/74532584/74532585/74532586/74532587/74532588/74532589/74532590/74532591/74532592/74532593/74532594/74532595/74532596/74532597/74532598/74532599/74532600/74532601/74532602/74532603/74532604/74532605/74532606/74532607/74532608/74532609/74532610/74532611/74532612/74532613/74532614/74532615/74532616/74532617/74532618/74532619/74532620/74532621/74532622/74532623/74532624/74532625/74532626/74532627/74532628/74532629/74532630/74532631/74532632/74532633/74532634/74532635/74532636/74532637/74532638/74532639/74532640/74532641/74532642/74532643/74532644/74532645/74532646/74532647/74532648/74532649/74532650/74532651/74532652/74532653/74532654/74532655/74532656/74532657/74532658/74532659/74532660/74532661/74532662/74532663/74532664/74532665/74532666/74532667/74532668/74532669/74532670/74532671/74532672/74532673/74532674/74532675/74532676/74532677/74532678/74532679/74532680/74532681/74532682/74532683/74532684/74532685/74532686/74532687/74532688/74532689/74532690/74532691/74532692/74532693/74532694/74532695/74532696/74532697/74532698/74532699/74532700/74532701/74532702/74532703/74532704/74532705/74532706/74532707/74532708/74532709/74532710/74532711/74532712/74532713/74532714/74532715/74532716/74532717/74532718/74532719/74532720/74532721/74532722/74532723/74532724/74532725/74532726/74532727/74532728/74532729/74532730/74532731/74532732/74532733/74532734/74532735/74532736/74532737/74532738/74532739/74532740/74532741/74532742/74532743/74532744/74532745/74532746/74532747/74532748/74532749/74532750/74532751/74532752/74532753/74532754/74532755/74532756/74532757/74532758/74532759/74532760/74532761/74532762/74532763/74532764/74532765/74532766/74532767/74532768/74532769/74532770/74532771/74532772/74532773/74532774/74532775/74532776/74532777/74532778/74532779/74532780/74532781/74532782/74532783/74532784/74532785/74532786/74532787/74532788/74532789/74532790/74532791/74532792/74532793/74532794/74532795/74532796/74532797/74532798/74532799/74532800/74532801/74532802/74532803/74532804/74532805/74532806/74532807/74532808/74532809/74532810/74532811/74532812/74532813/74532814/74532815/74532816/74532817/74532818/74532819/74532820/74532821/74532822/74532823/74532824/74532825/74532826/74532827/74532828/74532829/74532830/74532831/74532832/74532833/74532834/74532835/74532836/74532837/74532838/74532839/74532840/74532841/74532842/74532843/74532844/74532845/74532846/74532847/74532848/74532849/74532850/74532851/74532852/74532853/74532854/74532855/74532856/74532857/74532858/74532859/74532860/74532861/74532862/74532863/74532864/74532865/74532866/74532867/74532868/74532869/74532870/74532871/74532872/74532873/74532874/74532875/74532876/74532877/74532878/74532879/74532880/74532881/74532882/74532883/74532884/74532885/74532886/74532887/74532888/74532889/74532890/74532891/74532892/74532893/74532894/74532895/74532896/74532897/74532898/74532899/74532900/74532901/74532902/74532903/74532904/74532905/74532906/74532907/74532908/74532909/74532910/74532911/74532912/74532913/74532914/74532915/74532916/74532917/74532918/74532919/74532920/74532921/74532922/74532923/74532924/74532925/74532926/74532927/74532928/74532929/74532930/74532931/74532932/74532933/74532934/74532935/74532936/74532937/74532938/74532939/74532940/74532941/74532942/74532943/74532944/74532945/74532946/74532947/74532948/74532949/74532950/74532951/74532952/74532953/74532954/74532955/74532956/74532957/74532958/74532959/74532960/74532961/74532962/74532963/74532964/74532965/74532966/74532967/74532968/74532969/74532970/74532971/74532972/74532973/74532974/74532975/74532976/74532977/74532978/74532979/74532980/74532981/74532982/74532983/74532984/74532985/74532986/74532987/74532988/74532989/74532990/74532991/74532992/74532993/74532994/74532995/74532996/74532997/74532998/74532999/74533000/74533001/74533002/74533003/74533004/74533005/74533006/74533007/74533008/74533009/74533010/74533011/74533012/74533013/74533014/74533015/74533016/74533017/74533018/74533019/74533020/74533021/74533022/74533023/74533024/74533025/74533026/74533027/74533028/74533029/74533030/74533031/74533032/74533033/74533034/74533035/74533036/74533037/74533038/74533039/74533040/74533041/74533042/74533043/74533044/74533045/74533046/74533047/74533048/74533049/74533050/74533051/74533052/74533053/74533054/74533055/74533056/74533057/74533058/74533059/74533060/74533061/74533062/74533063/74533064/74533065/74533066/74533067/74533068/74533069/74533070/74533071/74533072/74533073/74533074/74533075/74533076/74533077/74533078/74533079/74533080/74533081/74533082/74533083/74533084/74533085/74533086/74533087/74533088/74533089/74533090/74533091/74533092/74533093/74533094/74533095/74533096/74533097/74533098/74533099/74533100/74533101/74533102/74533103/74533104/74533105/74533106/74533107/74533108/74533109/74533110/74533111/74533112/74533113/74533114/74533115/74533116/74533117/74533118/74533119/74533120/74533121/74533122/74533123/74533124/74533125/74533126/74533127/74533128/74533129/74533130/74533131/74533132/74533133/74533134/74533135/74533136/74533137/74533138/74533139/74533140/74533141/74533142/74533143/74533144/74533145/74533146/74533147/74533148/74533149/74533150/74533151/74533152/74533153/74533154/74533155/74533156/74533157/74533158/74533159/74533160/74533161/74533162/74533163/74533164/74533165/74533166/74533167/74533168/74533169/74533170/74533171/74533172/74533173/74533174/74533175/74533176/74533177/74533178/74533179/74533180/74533181/74533182/74533183/74533184/74533185/74533186/74533187/74533188/74533189/74533190/74533191/74533192/74533193/74533194/74533195/74533196/74533197/74533198/74533199/74533200/74533201/74533202/74533203/74533204/74533205/74533206/74533207/74533208/74533209/74533210/74533211/74533212/74533213/74533214/74533215/74533216/74533217/74533218/74533219/74533220/74533221/74533222/74533223/74533224/74533225/74533226/74533227/74533228/74533229/74533230/74533231/74533232/74533233/74533234/74533235/74533236/74533237/74533238/74533239/74533240/74533241/74533242/74533243/74533244/74533245/74533246/74533247/74533248/74533249/74533250/74533251/74533252/74533253/74533254/74533255/74533256/74533257/74533258/74533259/74533260/74533261/74533262/74533263/74533264/74533265/74533266/74533267/74533268/74533269/74533270/74533271/74533272/74533273/74533274/74533275/74533276/74533277/74533278/74533279/74533280/74533281/74533282/74533283/74533284/74533285/74533286/74533287/74533288/74533289/74533290/74533291/74533292/74533293/74533294/74533295/74533296/74533297/74533298/74533299/74533300/74533301/74533302/74533303/74533304/74533305/74533306/74533307/74533308/74533309/74533310/74533311/74533312/74533313/74533314/74533315/74533316/74533317/74533318/74533319/74533320/74533321/74533322/74533323/74533324/74533325/74533326/74533327/74533328/74533329/74533330/74533331/74533332/74533333/74533334/74533335/74533336/74533337/74533338/74533339/74533340/74533341/74533342/74533343/74533344/74533345/74533346/74533347/74533348/74533349/74533350/74533351/74533352/74533353/74533354/74533355/74533356/74533357/74533358/74533359/74533360/74533361/74533362/74533363/74533364/74533365/74533366/74533367/74533368/74533369/74533370/74533371/74533372/74533373/74533374/74533375/74533376/74533377/74533378/74533379/74533380/74533381/74533382/74533383/74533384/74533385/74533386/74533387/74533388/74533389/74533390/74533391/74533392/74533393/74533394/74533395/74533396/74533397/74533398/74533399/74533400/74533401/74533402/74533403/74533404/74533405/74533406/74533407/74533408/74533409/74533410/74533411/74533412/74533413/74533414/74533415/74533416/74533417/74533418/74533419/74533420/74533421/74533422/74533423/74533424/74533425/74533426/74533427/74533428/74533429/74533430/74533431/74533432/74533433/74533434/74533435/74533436/74533437/74533438/74533439/74533440/74533441/74533442/74533443/74533444/74533445/74533446/74533447/74533448/74533449/74533450/74533451/74533452/74533453/74533454/74533455/74533456/74533457/74533458/74533459/74533460/74533461/74533462/74533463/74533464/74533465/74533466/74533467/74533468/74533469/74533470/74533471/74533472/74533473/74533474/74533475/74533476/74533477/74533478/74533479/74533480/74533481/74533482/74533483/74533484/74533485/74533486/74533487/74533488/74533489/74533490/74533491/74533492/74533493/74533494/74533495/74533496/74533497/74533498/74533499/74533500/74533501/74533502/74533503/74533504/74533505/74533506/74533507/74533508/74533509/74533510/74533511/74533512/74533513/74533514/74533515/74533516/74533517/74533518/74533519/74533520/74533521/74533522/74533523/74533524/74533525/74533526/74533527/74533528/74533529/74533530/74533531/74533532/74533533/74533534/74533535/74533536/74533537/74533538/74533539/74533540/74533541/74533542/74533543/74533544/74533545/74533546/74533547/74533548/74533549/74533550/74533551/74533552/74533553/74533554/74533555/74533556/74533557/74533558/74533559/74533560/74533561/74533562/74533563/74533564/74533565/74533566/74533567/74533568/74533569/74533570/74533571/74533572/74533573/74533574/74533575/74533576/74533577/74533578/74533579/74533580/74533581/74533582/74533583/74533584/74533585/74533586/74533587/74533588/74533589/74533590/74533591/74533592/74533593/74533594/74533595/74533596/74533597/74533598/74533599/74533600/74533601/74533602/74533603/74533604/74533605/74533606/74533607/74533608/74533609/74533610/74533611/74533612/74533613/74533614/74533615/74533616/74533617/74533618/74533619/74533620/74533621/74533622/74533623/74533624/74533625/74533626/74533627/74533628/74533629/74533630/74533631/74533632/74533633/74533634/74533635/74533636/74533637/74533638/74533639/74533640/74533641/74533642/74533643/74533644/74533645/74533646/74533647/74533648/74533649/74533650/74533651/74533652/74533653/74533654/74533655/74533656/74533657/74533658/74533659/74533660/74533661/74533662/74533663/74533664/74533665/74533666/74533667/74533668/74533669/74533670/74533671/74533672/74533673/74533674/74533675/74533676/74533677/74533678/74533679/74533680/74533681/74533682/74533683/74533684/74533685/74533686/74533687/74533688/74533689/74533690/74533691/74533692/74533693/74533694/74533695/74533696/74533697/74533698/74533699/74533700/74533701/74533702/74533703/74533704/74533705/74533706/74533707/74533708/74533709/74533710/74533711/74533712/74533713/74533714/74533715/74533716/74533717/74533718/74533719/74533720/74533721/74533722/74533723/74533724/74533725/74533726/74533727/74533728/74533729/74533730/74533731/74533732/74533733/74533734/74533735/74533736/74533737/74533738/74533739/74533740/74533741/74533742/74533743/74533744/74533745/74533746/74533747/74533748/74533749/74533750/74533751/74533752/74533753/74533754/74533755/74533756/74533757/74533758/74533759/74533760/74533761/74533762/74533763/74533764/74533765/74533766/74533767/74533768/74533769/74533770/74533771/74533772/74533773/74533774/74533775/74533776/74533777/74533778/74533779/74533780/74533781/74533782/74533783/74533784/74533785/74533786/74533787/74533788/74533789/74533790/74533791/74533792/74533793/74533794/74533795/74533796/74533797/74533798/74533799/74533800/74533801/74533802/74533803/74533804/74533805/74533806/74533807/74533808/74533809/74533810/74533811/74533812/74533813/74533814/74533815/74533816/74533817/74533818/74533819/74533820/74533821/74533822/74533823/74533824/74533825/74533826/74533827/74533828/74533829/74533830/74533831/74533832/74533833/74533834/74533835/74533836/74533837/74533838/74533839/74533840/74533841/74533842/74533843/74533844/74533845/74533846/74533847/74533848/74533849/74533850/74533851/74533852/74533853/74533854/74533855/74533856/74533857/74533858/74533859/74533860/74533861/74533862/74533863/74533864/74533865/74533866/74533867/74533868/74533869/74533870/74533871/74533872/74533873/74533874/74533875/74533876/74533877/74533878/74533879/74533880/74533881/74533882/74533883/74533884/74533885/74533886/74533887/74533888/74533889/74533890/74533891/74533892/74533893/74533894/74533895/74533896/74533897/74533898/74533899/74533900/74533901/74533902/74533903/74533904/74533905/74533906/74533907/74533908/74533909/74533910/74533911/74533912/74533913/74533914/74533915/74533916/74533917/74533918/74533919/74533920/74533921/74533922/74533923/74533924/74533925/74533926/74533927/74533928/74533929/74533930/74533931/74533932/74533933/74533934/74533935/74533936/74533937/74533938/74533939/74533940/74533941/74533942/74533943/74533944/74533945/74533946/74533947/74533948/74533949/74533950/74533951/74533952/74533953/74533954/74533955/74533956/74533957/74533958/74533959/74533960/74533961/74533962/74533963/74533964/74533965/74533966/74533967/74533968/74533969/74533970/74533971/74533972/74533973/74533974/74533975/74533976/74533977/74533978/74533979/74533980/74533981/74533982/74533983/74533984/74533985/74533986/74533987/74533988/74533989/74533990/74533991/74533992/74533993/74533994/74533995/74533996/74533997/74533998/74533999/74534000/74534001/74534002/74534003/74534004/74534005/74534006/74534007/74534008/74534009/74534010/74534011/74534012/74534013/74534014/74534015/74534016/74534017/74534018/74534019/74534020/74534021/74534022/74534023/74534024/74534025/74534026/74534027/74534028/74534029/74534030/74534031/74534032/74534033/74534034/74534035/74534036/74534037/74534038/74534039/74534040/74534041/74534042/74534043/74534044/74534045/74534046/74534047/74534048/74534049/74534050/74534051/74534052/74534053/74534054/74534055/74534056/74534057/74534058/74534059/74534060/74534061/74534062/74534063/74534064/74534065/74534066/74534067/74534068/74534069/74534070/74534071/74534072/74534073/74534074/74534075/74534076/74534077/74534078/74534079/74534080/74534081/74534082/74534083/74534084/74534085/74534086/74534087/74534088/74534089/74534090/74534091/74534092/74534093/74534094/74534095/74534096/74534097/74534098/74534099/74534100/74534101/74534102/74534103/74534104/74534105/74534106/74534107/74534108/74534109/74534110/74534111/74534112/74534113/74534114/74534115/74534116/74534117/74534118/74534119/74534120/74534121/74534122/74534123/74534124/74534125/74534126/74534127/74534128/74534129/74534130/74534131/74534132/74534133/74534134/74534135/74534136/74534137/74534138/74534139/74534140/74534141/74534142/74534143/74534144/74534145/74534146/74534147/74534148/74534149/74534150/74534151/74534152/74534153/74534154/74534155/74534156/74534157/74534158/74534159/74534160/74534161/74534162/74534163/74534164/74534165/74534166/74534167/74534168/74534169/74534170/74534171/74534172/74534173/74534174/74534175/74534176/74534177/74534178/74534179/74534180/74534181/74534182/74534183/74534184/74534185/74534186/74534187/74534188/74534189/74534190/74534191/74534192/74534193/74534194/74534195/74534196/74534197/74534198/74534199/74534200/74534201/74534202/74534203/74534204/74534205/74534206/74534207/74534208/74534209/74534210/74534211/74534212/74534213/74534214/74534215/74534216/74534217/74534218/74534219/74534220/74534221/74534222/74534223/74534224/74534225/74534226/74534227/74534228/74534229/74534230/74534231/74534232/74534233/74534234/74534235/74534236/74534237/74534238/74534239/74534240/74534241/74534242/74534243/74534244/74534245/74534246/74534247/74534248/74534249/74534250/74534251/74534252/74534253/74534254/74534255/74534256/74534257/74534258/74534259/74534260/74534261/74534262/74534263/74534264/74534265/74534266/74534267/74534268/74534269/74534270/74534271/74534272/74534273/74534274/74534275/74534276/74534277/74534278/74534279/74534280/74534281/74534282/74534283/74534284/74534285/74534286/74534287/74534288/74534289/74534290/74534291/74534292/74534293/74534294/74534295/74534296/74534297/74534298/74534299/74534300/74534301/74534302/74534303/74534304/74534305/74534306/74534307/74534308/74534309/74534310/74534311/74534312/74534313/74534314/74534315/74534316/74534317/74534318/74534319/74534320/74534321/74534322/74534323/74534324/74534325/74534326/74534327/74534328/74534329/74534330/74534331/74534332/74534333/74534334/74534335/74534336/74534337/74534338/74534339/74534340/74534341/74534342/74534343/74534344/74534345/74534346/74534347/74534348/74534349/74534350/74534351/74534352/74534353/74534354/74534355/74534356/74534357/74534358/74534359/74534360/74534361/74534362/74534363/74534364/74534365/74534366/74534367/74534368/74534369/74534370/74534371/74534372/74534373/74534374/74534375/74534376/74534377/74534378/74534379/74534380/74534381/74534382/74534383/74534384/74534385/74534386/74534387/74534388/74534389/74534390/74534391/74534392/74534393/74534394/74534395/74534396/74534397/74534398/74534399/74534400/74534401/74534402/74534403/74534404/74534405/74534406/74534407/74534408/74534409/74534410/74534411/74534412/74534413/74534414/74534415/74534416/74534417/74534418/74534419/74534420/74534421/74534422/74534423/74534424/74534425/74534426/74534427/74534428/74534429/74534430/74534431/74534432/74534433/74534434/74534435/74534436/74534437/74534438/74534439/74534440/74534441/74534442/74534443/74534444/74534445/74534446/74534447/74534448/74534449/74534450/74534451/74534452/74534453/74534454/74534455/74534456/74534457/74534458/74534459/74534460/74534461/74534462/74534463/74534464/74534465/74534466/74534467/74534468/74534469/74534470/74534471/74534472/74534473/74534474/74534475/74534476/74534477/74534478/74534479/74534480/74534481/74534482/74534483/74534484/74534485/74534486/74534487/74534488/74534489/74534490/74534491/74534492/74534493/74534494/74534495/74534496/74534497/74534498/74534499/74534500/74534501/74534502/74534503/74534504/74534505/74534506/74534507/74534508/74534509/74534510/74534511/74534512/74534513/74534514/74534515/74534516/74534517/74534518/74534519/74534520/74534521/74534522/74534523/74534524/74534525/74534526/74534527/74534528/74534529/74534530/74534531/74534532/74534533/74534534/74534535/74534536/74534537/74534538/74534539/74534540/74534541/74534542/74534543/74534544/74534545/74534546/74534547/74534548/74534549/74534550/74534551/74534552/74534553/74534554/74534555/74534556/74534557/74534558/74534559/74534560/74534561/74534562/74534563/74534564/74534565/74534566/74534567/74534568/74534569/74534570/74534571/74534572/74534573/74534574/74534575/74534576/74534577/74534578/74534579/74534580/74534581/74534582/74534583/74534584/74534585/74534586/74534587/74534588/74534589/74534590/74534591/74534592/74534593/74534594/74534595/74534596/74534597/74534598/74534599/74534600/74534601/74534602/74534603/74534604/74534605/74534606/74534607/74534608/74534609/74534610/74534611/74534612/74534613/74534614/74534615/74534616/74534617/74534618/74534619/74534620/74534621/74534622/74534623/74534624/74534625/74534626/74534627/74534628/74534629/74534630/74534631/74534632/74534633/74534634/74534635/74534636/74534637/74534638/74534639/74534640/74534641/74534642/74534643/74534644/74534645/74534646/74534647/74534648/74534649/74534650/74534651/74534652/74534653/74534654/74534655/74534656/74534657/74534658/74534659/74534660/74534661/74534662/74534663/74534664/74534665/74534666/74534667/74534668/74534669/74534670/74534671/74534672/74534673/74534674/74534675/74534676/74534677/74534678/74534679/74534680/74534681/74534682/74534683/74534684/74534685/74534686/74534687/74534688/74534689/74534690/74534691/74534692/74534693/74534694/74534695/74534696/74534697/74534698/74534699/74534700/74534701/74534702/74534703/74534704/74534705/74534706/74534707/74534708/74534709/74534710/74534711/74534712/74534713/74534714/74534715/74534716/74534717/74534718/74534719/74534720/74534721/74534722/74534723/74534724/74534725/74534726/74534727/74534728/74534729/74534730/74534731/74534732/74534733/74534734/74534735/74534736/74534737/74534738/74534739/74534740/74534741/74534742/74534743/74534744/74534745/74534746/74534747/74534748/74534749/74534750/74534751/74534752/74534753/74534754/74534755/74534756/74534757/74534758/74534759/74534760/74534761/74534762/74534763/74534764/74534765/74534766/74534767/74534768/74534769/74534770/74534771/74534772/74534773/74534774/74534775/74534776/74534777/74534778/74534779/74534780/74534781/74534782/74534783/74534784/74534785/74534786/74534787/74534788/74534789/74534790/74534791/74534792/74534793/74534794/74534795/74534796/74534797/74534798/74534799/74534800/74534801/74534802/74534803/74534804/74534805/74534806/74534807/74534808/74534809/74534810/74534811/74534812/74534813/74534814/74534815/74534816/74534817/74534818/74534819/74534820/74534821/74534822/74534823/74534824/74534825/74534826/74534827/74534828/74534829/74534830/74534831/74534832/74534833/74534834/74534835/74534836/74534837/74534838/74534839/74534840/74534841/74534842/74534843/74534844/74534845/74534846/74534847/74534848/74534849/74534850/74534851/74534852/74534853/74534854/74534855/74534856/74534857/74534858/74534859/74534860/74534861/74534862/74534863/74534864/74534865/74534866/74534867/74534868/74534869/74534870/74534871/74534872/74534873/74534874/74534875/74534876/74534877/74534878/74534879/74534880/74534881/74534882/74534883/74534884/74534885/74534886/74534887/74534888/74534889/74534890/74534891/74534892/74534893/74534894/74534895/74534896/74534897/74534898/74534899/74534900/74534901/74534902/74534903/74534904/74534905/74534906/74534907/74534908/74534909/74534910/74534911/74534912/74534913/74534914/74534915/74534916/74534917/74534918/74534919/74534920/74534921/74534922/74534923/74534924/74534925/74534926/74534927/74534928/74534929/74534930/74534931/74534932/74534933/74534934/74534935/74534936/74534937/74534938/74534939/74534940/74534941/74534942/74534943/74534944/74534945/74534946/74534947/74534948/74534949/74534950/74534951/74534952/74534953/74534954/74534955/74534956/74534957/74534958/74534959/74534960/74534961/74534962/74534963/74534964/74534965/74534966/74534967/74534968/74534969/74534970/74534971/74534972/74534973/74534974/74534975/74534976/74534977/74534978/74534979/74534980/74534981/74534982/74534983/74534984/74534985/74534986/74534987/74534988/74534989/74534990/74534991/74534992/74534993/74534994/74534995/74534996/74534997/74534998/74534999/74535000/74535001/74535002/74535003/74535004/74535005/74535006/74535007/74535008/74535009/74535010/74535011/74535012/74535013/74535014/74535015/74535016/74535017/74535018/74535019/74535020/74535021/74535022/74535023/74535024/74535025/74535026/74535027/74535028/74535029/74535030/74535031/74535032/74535033/74535034/74535035/74535036/74535037/74535038/74535039/74535040/74535041/74535042/74535043/74535044/74535045/74535046/74535047/74535048/74535049/74535050/74535051/74535052/74535053/74535054/74535055/74535056/74535057/74535058/74535059/74535060/74535061/74535062/74535063/74535064/74535065/74535066/74535067/74535068/74535069/74535070/74535071/74535072/74535073/74535074/74535075/74535076/74535077/74535078/74535079/74535080/74535081/74535082/74535083/74535084/74535085/74535086/74535087/74535088/74535089/74535090/74535091/74535092/74535093/74535094/74535095/74535096/74535097/74535098/74535099/74535100/74535101/74535102/74535103/74535104/74535105/74535106/74535107/74535108/74535109/74535110/74535111/74535112/74535113/74535114/74535115/74535116/74535117/74535118/74535119/74535120/74535121/74535122/74535123/74535124/74535125/74535126/74535127/74535128/74535129/74535130/74535131/74535132/74535133/74535134/74535135/74535136/74535137/74535138/74535139/74535140/74535141/74535142/74535143/74535144/74535145/74535146/74535147/74535148/74535149/74535150/74535151/74535152/74535153/74535154/74535155/74535156/74535157/74535158/74535159/74535160/74535161/74535162/74535163/74535164/74535165/74535166/74535167/74535168/74535169/74535170/74535171/74535172/74535173/74535174/74535175/74535176/74535177/74535178/74535179/74535180/74535181/74535182/74535183/74535184/74535185/74535186/74535187/74535188/74535189/74535190/74535191/74535192/74535193/74535194/74535195/74535196/74535197/74535198/74535199/74535200/74535201/74535202/74535203/74535204/74535205/74535206/74535207/74535208/74535209/74535210/74535211/74535212/74535213/74535214/74535215/74535216/74535217/74535218/74535219/74535220/74535221/74535222/74535223/74535224/74535225/74535226/74535227/74535228/74535229/74535230/74535231/74535232/74535233/74535234/74535235/74535236/74535237/74535238/74535239/74535240/74535241/74535242/74535243/74535244/74535245/74535246/74535247/74535248/74535249/74535250/74535251/74535252/74535253/74535254/74535255/74535256/74535257/74535258/74535259/74535260/74535261/74535262/74535263/74535264/74535265/74535266/74535267/74535268/74535269/74535270/74535271/74535272/74535273/74535274/74535275/74535276/74535277/74535278/74535279/74535280/74535281/74535282/74535283/74535284/74535285/74535286/74535287/74535288/74535289/74535290/74535291/74535292/74535293/74535294/74535295/74535296/74535297/74535298/74535299/74535300/74535301/74535302/74535303/74535304/74535305/74535306/74535307/74535308/74535309/74535310/74535311/74535312/74535313/74535314/74535315/74535316/74535317/74535318/74535319/74535320/74535321/74535322/74535323/74535324/74535325/74535326/74535327/74535328/74535329/74535330/74535331/74535332/74535333/74535334/74535335/74535336/74535337/74535338/74535339/74535340/74535341/74535342/74535343/74535344/74535345/74535346/74535347/74535348/74535349/74535350/74535351/74535352/74535353/74535354/74535355/74535356/74535357/74535358/74535359/74535360/74535361/74535362/74535363/74535364/74535365/74535366/74535367/74535368/74535369/74535370/74535371/74535372/74535373/74535374/74535375/74535376/74535377/74535378/74535379/74535380/74535381/74535382/74535383/74535384/74535385/74535386/74535387/74535388/74535389/74535390/74535391/74535392/74535393/74535394/74535395/74535396/74535397/74535398/74535399/74535400/74535401/74535402/74535403/74535404/74535405/74535406/74535407/74535408/74535409/74535410/74535411/74535412/74535413/74535414/74535415/74535416/74535417/74535418/74535419/74535420/74535421/74535422/74535423/74535424/74535425/74535426/74535427/74535428/74535429/74535430/74535431/74535432/74535433/74535434/74535435/74535436/74535437/74535438/74535439/74535440/74535441/74535442/74535443/74535444/74535445/74535446/74535447/74535448/74535449/74535450/74535451/74535452/74535453/74535454/74535455/74535456/74535457/74535458/74535459/74535460/74535461/74535462/74535463/74535464/74535465/74535466/74535467/74535468/74535469/74535470/74535471/74535472/74535473/74535474/74535475/74535476/74535477/74535478/74535479/74535480/74535481/74535482/74535483/74535484/74535485/74535486/74535487/74535488/74535489/74535490/74535491/74535492/74535493/74535494/74535495/74535496/74535497/74535498/74535499/74535500/74535501/74535502/74535503/74535504/74535505/74535506/74535507/74535508/74535509/74535510/74535511/74535512/74535513/74535514/74535515/74535516/74535517/74535518/74535519/74535520/74535521/74535522/74535523/74535524/74535525/74535526/74535527/74535528/74535529/74535530/74535531/74535532/74535533/74535534/74535535/74535536/74535537/74535538/74535539/74535540/74535541/74535542/74535543/74535544/74535545/74535546/74535547/74535548/74535549/74535550/74535551/74535552/74535553/74535554/74535555/74535556/74535557/74535558/74535559/74535560/74535561/74535562/74535563/74535564/74535565/74535566/74535567/74535568/74535569/74535570/74535571/74535572/74535573/74535574/74535575/74535576/74535577/74535578/74535579/74535580/74535581/74535582/74535583/74535584/74535585/74535586/74535587/74535588/74535589/74535590/74535591/74535592/74535593/74535594/74535595/74535596/74535597/74535598/74535599/74535600/74535601/74535602/74535603/74535604/74535605/74535606/74535607/74535608/74535609/74535610/74535611/74535612/74535613/74535614/74535615/74535616/74535617/74535618/74535619/74535620/74535621/74535622/74535623/74535624/74535625/74535626/74535627/74535628/74535629/74535630/74535631/74535632/74535633/74535634/74535635/74535636/74535637/74535638/74535639/74535640/74535641/74535642/74535643/74535644/74535645/74535646/74535647/74535648/74535649/74535650/74535651/74535652/74535653/74535654/74535655/74535656/74535657/74535658/74535659/74535660/74535661/74535662/74535663/74535664/74535665/74535666/74535667/74535668/74535669/74535670/74535671/74535672/74535673/74535674/74535675/74535676/74535677/74535678/74535679/74535680/74535681/74535682/74535683/74535684/74535685/74535686/74535687/74535688/74535689/74535690/74535691/74535692/74535693/74535694/74535695/74535696/74535697/74535698/74535699/74535700/74535701/74535702/74535703/74535704/74535705/74535706/74535707/74535708/74535709/74535710/74535711/74535712/74535713/74535714/74535715/74535716/74535717/74535718/74535719/74535720/74535721/74535722/74535723/74535724/74535725/74535726/74535727/74535728/74535729/74535730/74535731/74535732/74535733/74535734/74535735/74535736/74535737/74535738/74535739/74535740/74535741/74535742/74535743/74535744/74535745/74535746/74535747/74535748/74535749/74535750/74535751/74535752/74535753/74535754/74535755/74535756/74535757/74535758/74535759/74535760/74535761/74535762/74535763/74535764/74535765/74535766/74535767/74535768/74535769/74535770/74535771/74535772/74535773/74535774/74535775/74535776/74535777/74535778/74535779/74535780/74535781/74535782/74535783/74535784/74535785/74535786/74535787/74535788/74535789/74535790/74535791/74535792/74535793/74535794/74535795/74535796/74535797/74535798/74535799/74535800/74535801/74535802/74535803/74535804/74535805/74535806/74535807/74535808/74535809/74535810/74535811/74535812/74535813/74535814/74535815/74535816/74535817/74535818/74535819/74535820/74535821/74535822/74535823/74535824/74535825/74535826/74535827/74535828/74535829/74535830/74535831/74535832/74535833/74535834/74535835/74535836/74535837/74535838/74535839/74535840/74535841/74535842/74535843/74535844/74535845/74535846/74535847/74535848/74535849/74535850/74535851/74535852/74535853/74535854/74535855/74535856/74535857/74535858/74535859/74535860/74535861/74535862/74535863/74535864/74535865/74535866/74535867/74535868/74535869/74535870/74535871/74535872/74535873/74535874/74535875/74535876/74535877/74535878/74535879/74535880/74535881/74535882/74535883/74535884/74535885/74535886/74535887/74535888/74535889/74535890/74535891/74535892/74535893/74535894/74535895/74535896/74535897/74535898/74535899/74535900/74535901/74535902/74535903/74535904/74535905/74535906/74535907/74535908/74535909/74535910/74535911/74535912/74535913/74535914/74535915/74535916/74535917/74535918/74535919/74535920/74535921/74535922/74535923/74535924/74535925/74535926/74535927/74535928/74535929/74535930/74535931/74535932/74535933/74535934/74535935/74535936/74535937/74535938/74535939/74535940/74535941/74535942/74535943/74535944/74535945/74535946/74535947/74535948/74535949/74535950/74535951/74535952/74535953/74535954/74535955/74535956/74535957/74535958/74535959/74535960/74535961/74535962/74535963/74535964/74535965/74535966/74535967/74535968/74535969/74535970/74535971/74535972/74535973/74535974/74535975/74535976/74535977/74535978/74535979/74535980/74535981/74535982/74535983/74535984/74535985/74535986/74535987/74535988/74535989/74535990/74535991/74535992/74535993/74535994/74535995/74535996/74535997/74535998/74535999/74536000/74536001/74536002/74536003/74536004/74536005/74536006/74536007/74536008/74536009/74536010/74536011/74536012/74536013/74536014/74536015/74536016/74536017/74536018/74536019/74536020/74536021/74536022/74536023/74536024/74536025/74536026/74536027/74536028/74536029/74536030/74536031/74536032/74536033/74536034/74536035/74536036/74536037/74536038/74536039/74536040/74536041/74536042/74536043/74536044/74536045/74536046/74536047/74536048/74536049/74536050/74536051/74536052/74536053/74536054/74536055/74536056/74536057/74536058/74536059/74536060/74536061/74536062/74536063/74536064/74536065/74536066/74536067/74536068/74536069/74536070/74536071/74536072/74536073/74536074/74536075/74536076/74536077/74536078/74536079/74536080/74536081/74536082/74536083/74536084/74536085/74536086/74536087/74536088/74536089/74536090/74536091/74536092/74536093/74536094/74536095/74536096/74536097/74536098/74536099/74536100/74536101/74536102/74536103/74536104/74536105/74536106/74536107/74536108/74536109/74536110/74536111/74536112/74536113/74536114/74536115/74536116/74536117/74536118/74536119/74536120/74536121/74536122/74536123/74536124/74536125/74536126/74536127/74536128/74536129/74536130/74536131/74536132/74536133/74536134/74536135/74536136/74536137/74536138/74536139/74536140/74536141/74536142/74536143/74536144/74536145/74536146/74536147/74536148/74536149/74536150/74536151/74536152/74536153/74536154/74536155/74536156/74536157/74536158/74536159/74536160/74536161/74536162/74536163/74536164/74536165/74536166/74536167/74536168/74536169/74536170/74536171/74536172/74536173/74536174/74536175/74536176/74536177/74536178/74536179/74536180/74536181/74536182/74536183/74536184/74536185/74536186/74536187/74536188/74536189/74536190/74536191/74536192/74536193/74536194/74536195/74536196/74536197/74536198/74536199/74536200/74536201/74536202/74536203/74536204/74536205/74536206/74536207/74536208/74536209/74536210/74536211/74536212/74536213/74536214/74536215/74536216/74536217/74536218/74536219/74536220/74536221/74536222/74536223/74536224/74536225/74536226/74536227/74536228/74536229/74536230/74536231/74536232/74536233/74536234/74536235/74536236/74536237/74536238/74536239/74536240/74536241/74536242/74536243/74536244/74536245/74536246/74536247/74536248/74536249/74536250/74536251/74536252/74536253/74536254/74536255/74536256/74536257/74536258/74536259/74536260/74536261/74536262/74536263/74536264/74536265/74536266/74536267/74536268/74536269/74536270/74536271/74536272/74536273/74536274/74536275/74536276/74536277/74536278/74536279/74536280/74536281/74536282/74536283/74536284/74536285/74536286/74536287/74536288/74536289/74536290/74536291/74536292/74536293/74536294/74536295/74536296/74536297/74536298/74536299/74536300/74536301/74536302/74536303/74536304/74536305/74536306/74536307/74536308/74536309/74536310/74536311/74536312/74536313/74536314/74536315/74536316/74536317/74536318/74536319/74536320/74536321/74536322/74536323/74536324/74536325/74536326/74536327/74536328/74536329/74536330/74536331/74536332/74536333/74536334/74536335/74536336/74536337/74536338/74536339/74536340/74536341/74536342/74536343/74536344/74536345/74536346/74536347/74536348/74536349/74536350/74536351/74536352/74536353/74536354/74536355/74536356/74536357/74536358/74536359/74536360/74536361/74536362/74536363/74536364/74536365/74536366/74536367/74536368/74536369/74536370/74536371/74536372/74536373/74536374/74536375/74536376/74536377/74536378/74536379/74536380/74536381/74536382/74536383/74536384/74536385/74536386/74536387/74536388/74536389/74536390/74536391/74536392/74536393/74536394/74536395/74536396/74536397/74536398/74536399/74536400/74536401/74536402/74536403/74536404/74536405/74536406/74536407/74536408/74536409/74536410/74536411/74536412/74536413/74536414/74536415/74536416/74536417/74536418/74536419/74536420/74536421/74536422/74536423/74536424/74536425/74536426/74536427/74536428/74536429/74536430/74536431/74536432/74536433/74536434/74536435/74536436/74536437/74536438/74536439/74536440/74536441/74536442/74536443/74536444/74536445/74536446/74536447/74536448/74536449/74536450/74536451/74536452/74536453/74536454/74536455/74536456/74536457/74536458/74536459/74536460/74536461/74536462/74536463/74536464/74536465/74536466/74536467/74536468/74536469/74536470/74536471/74536472/74536473/74536474/74536475/74536476/74536477/74536478/74536479/74536480/74536481/74536482/74536483/74536484/74536485/74536486/74536487/74536488/74536489/74536490/74536491/74536492/74536493/74536494/74536495/74536496/74536497/74536498/74536499/74536500/74536501/74536502/74536503/74536504/74536505/74536506/74536507/74536508/74536509/74536510/74536511/74536512/74536513/74536514/74536515/74536516/74536517/74536518/74536519/74536520/74536521/74536522/74536523/74536524/74536525/74536526/74536527/74536528/74536529/74536530/74536531/74536532/74536533/74536534/74536535/74536536/74536537/74536538/74536539/74536540/74536541/74536542/74536543/74536544/74536545/74536546/74536547/74536548/74536549/74536550/74536551/74536552/74536553/74536554/74536555/74536556/74536557/74536558/74536559/74536560/74536561/74536562/74536563/74536564/74536565/74536566/74536567/74536568/74536569/74536570/74536571/74536572/74536573/74536574/74536575/74536576/74536577/74536578/74536579/74536580/74536581/74536582/74536583/74536584/74536585/74536586/74536587/74536588/74536589/74536590/74536591/74536592/74536593/74536594/74536595/74536596/74536597/74536598/74536599/74536600/74536601/74536602/74536603/74536604/74536605/74536606/74536607/74536608/74536609/74536610/74536611/74536612/74536613/74536614/74536615/74536616/74536617/74536618/74536619/74536620/74536621/74536622/74536623/74536624/74536625/74536626/74536627/74536628/74536629/74536630/74536631/74536632/74536633/74536634/74536635/74536636/74536637/74536638/74536639/74536640/74536641/74536642/74536643/74536644/74536645/74536646/74536647/74536648/74536649/74536650/74536651/74536652/74536653/74536654/74536655/74536656/74536657/74536658/74536659/74536660/74536661/74536662/74536663/74536664/74536665/74536666/74536667/74536668/74536669/74536670/74536671/74536672/74536673/74536674/74536675/74536676/74536677/74536678/74536679/74536680/74536681/74536682/74536683/74536684/74536685/74536686/74536687/74536688/74536689/74536690/74536691/74536692/74536693/74536694/74536695/74536696/74536697/74536698/74536699/74536700/74536701/74536702/74536703/74536704/74536705/74536706/74536707/74536708/74536709/74536710/74536711/74536712/74536713/74536714/74536715/74536716/74536717/74536718/74536719/74536720/74536721/74536722/74536723/74536724/74536725/74536726/74536727/74536728/74536729/74536730/74536731/74536732/74536733/74536734/74536735/74536736/74536737/74536738/74536739/74536740/74536741/74536742/74536743/74536744/74536745/74536746/74536747/74536748/74536749/74536750/74536751/74536752/74536753/74536754/74536755/74536756/74536757/74536758/74536759/74536760/74536761/74536762/74536763/74536764/74536765/74536766/74536767/74536768/74536769/74536770/74536771/74536772/74536773/74536774/74536775/74536776/74536777/74536778/74536779/74536780/74536781/74536782/74536783/74536784/74536785/74536786/74536787/74536788/74536789/74536790/74536791/74536792/74536793/74536794/74536795/74536796/74536797/74536798/74536799/74536800/74536801/74536802/74536803/74536804/74536805/74536806/74536807/74536808/74536809/74536810/74536811/74536812/74536813/74536814/74536815/74536816/74536817/74536818/74536819/74536820/74536821/74536822/74536823/74536824/74536825/74536826/74536827/74536828/74536829/74536830/74536831/74536832/74536833/74536834/74536835/74536836/74536837/74536838/74536839/74536840/74536841/74536842/74536843/74536844/74536845/74536846/74536847/74536848/74536849/74536850/74536851/74536852/74536853/74536854/74536855/74536856/74536857/74536858/74536859/74536860/74536861/74536862/74536863/74536864/74536865/74536866/74536867/74536868/74536869/74536870/74536871/74536872/74536873/74536874/74536875/74536876/74536877/74536878/74536879/74536880/74536881/74536882/74536883/74536884/74536885/74536886/74536887/74536888/74536889/74536890/74536891/74536892/74536893/74536894/74536895/74536896/74536897/74536898/74536899/74536900/74536901/74536902/74536903/74536904/74536905/74536906/74536907/74536908/74536909/74536910/74536911/74536912/74536913/74536914/74536915/74536916/74536917/74536918/74536919/74536920/74536921/74536922/74536923/74536924/74536925/74536926/74536927/74536928/74536929/74536930/74536931/74536932/74536933/74536934/74536935/74536936/74536937/74536938/74536939/74536940/74536941/74536942/74536943/74536944/74536945/74536946/74536947/74536948/74536949/74536950/74536951/74536952/74536953/74536954/74536955/74536956/74536957/74536958/74536959/74536960/74536961/74536962/74536963/74536964/74536965/74536966/74536967/74536968/74536969/74536970/74536971/74536972/74536973/74536974/74536975/74536976/74536977/74536978/74536979/74536980/74536981/74536982/74536983/74536984/74536985/74536986/74536987/74536988/74536989/74536990/74536991/74536992/74536993/74536994/74536995/74536996/74536997/74536998/74536999/74537000/74537001/74537002/74537003/74537004/74537005/74537006/74537007/74537008/74537009/74537010/74537011/74537012/74537013/74537014/74537015/74537016/74537017/74537018/74537019/74537020/74537021/74537022/74537023/74537024/74537025/74537026/74537027/74537028/74537029/74537030/74537031/74537032/74537033/74537034/74537035/74537036/74537037/74537038/74537039/74537040/74537041/74537042/74537043/74537044/74537045/74537046/74537047/74537048/74537049/74537050/74537051/74537052/74537053/74537054/74537055/74537056/74537057/74537058/74537059/74537060/74537061/74537062/74537063/74537064/74537065/74537066/74537067/74537068/74537069/74537070/74537071/74537072/74537073/74537074/74537075/74537076/74537077/74537078/74537079/74537080/74537081/74537082/74537083/74537084/74537085/74537086/74537087/74537088/74537089/74537090/74537091/74537092/74537093/74537094/74537095/74537096/74537097/74537098/74537099/74537100/74537101/74537102/74537103/74537104/74537105/74537106/74537107/74537108/74537109/74537110/74537111/74537112/74537113/74537114/74537115/74537116/74537117/74537118/74537119/74537120/74537121/74537122/74537123/74537124/74537125/74537126/74537127/74537128/74537129/74537130/74537131/74537132/74537133/74537134/74537135/74537136/74537137/74537138/74537139/74537140/74537141/74537142/74537143/74537144/74537145/74537146/74537147/74537148/74537149/74537150/74537151/74537152/74537153/74537154/74537155/74537156/74537157/74537158/74537159/74537160/74537161/74537162/74537163/74537164/74537165/74537166/74537167/74537168/74537169/74537170/74537171/74537172/74537173/74537174/74537175/74537176/74537177/74537178/74537179/74537180/74537181/74537182/74537183/74537184/74537185/74537186/74537187/74537188/74537189/74537190/74537191/74537192/74537193/74537194/74537195/74537196/74537197/74537198/74537199/74537200/74537201/74537202/74537203/74537204/74537205/74537206/74537207/74537208/74537209/74537210/74537211/74537212/74537213/74537214/74537215/74537216/74537217/74537218/74537219/74537220/74537221/74537222/74537223/74537224/74537225/74537226/74537227/74537228/74537229/74537230/74537231/74537232/74537233/74537234/74537235/74537236/74537237/74537238/74537239/74537240/74537241/74537242/74537243/74537244/74537245/74537246/74537247/74537248/74537249/74537250/74537251/74537252/74537253/74537254/74537255/74537256/74537257/74537258/74537259/74537260/74537261/74537262/74537263/74537264/74537265/74537266/74537267/74537268/74537269/74537270/74537271/74537272/74537273/74537274/74537275/74537276/74537277/74537278/74537279/74537280/74537281/74537282/74537283/74537284/74537285/74537286/74537287/74537288/74537289/74537290/74537291/74537292/74537293/74537294/74537295/74537296/74537297/74537298/74537299/74537300/74537301/74537302/74537303/74537304/74537305/74537306/74537307/74537308/74537309/74537310/74537311/74537312/74537313/74537314/74537315/74537316/74537317/74537318/74537319/74537320/74537321/74537322/74537323/74537324/74537325/74537326/74537327/74537328/74537329/74537330/74537331/74537332/74537333/74537334/74537335/74537336/74537337/74537338/74537339/74537340/74537341/74537342/74537343/74537344/74537345/74537346/74537347/74537348/74537349/74537350/74537351/74537352/74537353/74537354/74537355/74537356/74537357/74537358/74537359/74537360/74537361/74537362/74537363/74537364/74537365/74537366/74537367/74537368/74537369/74537370/74537371/74537372/74537373/74537374/74537375/74537376/74537377/74537378/74537379/74537380/74537381/74537382/74537383/74537384/74537385/74537386/74537387/74537388/74537389/74537390/74537391/74537392/74537393/74537394/74537395/74537396/74537397/74537398/74537399/74537400/74537401/74537402/74537403/74537404/74537405/74537406/74537407/74537408/74537409/74537410/74537411/74537412/74537413/74537414/74537415/74537416/74537417/74537418/74537419/74537420/74537421/74537422/74537423/74537424/74537425/74537426/74537427/74537428/74537429/74537430/74537431/74537432/74537433/74537434/74537435/74537436/74537437/74537438/74537439/74537440/74537441/74537442/74537443/74537444/74537445/74537446/74537447/74537448/74537449/74537450/74537451/74537452/7453done
mke2fs 1.41.3 (12-Oct-2008)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir

========================================
```

---

### Post by Rocket2DMn on 2009-04-27
If you are running GParted, you should be able to Delete the existing partition, then format the new one to NTFS.  Are you trying from the command line?

You can always plug it into a Windows box and format NTFS from there as well.

---

### Post by qjmoss on 2009-04-27
Okay, i've deleted my old partition.

Now under where i select my new format, ntfs is grayed out.

I installed the ntfsprogs too, as someone said.

humph =/

---

### Post by mb_webguy on 2009-04-27
Try running ntfs-config and make sure you have write support for external volumes enabled.

---

### Post by qjmoss on 2009-04-27
Okay, I installed ntfs-config and ran it.. it said support wasent enabled for externals.

I've enabled it.


is there a way in gparted that I can skip the process where it checks all drives.

It's takes an extended period of time, and I lose response to my system for that time...

---

### Post by Rocket2DMn on 2009-04-27
Were you able to work it out?  How many drives do you actually have?  I would unplug everything except the external you are using if for no other reason than to help prevent confusion.  You should be able to format with write enabled to externals and ntfsprogs installed.  Again, if all else fails you can format from a Windows computer as NTFS is a native Windows filesystem.

---

### Post by qjmoss on 2009-04-27
I've formatted my external to ntfs, i hope this solves my torrent failing issue.

I'm just a little afraid that it's not going to be compatible with my Linux system.


Is there any drivers that i need to install to make it compatible?:P

---

### Post by mb_webguy on 2009-04-27
> **qjmoss said:**
> I've formatted my external to ntfs, i hope this solves my torrent failing issue.

I'm just a little afraid that it's not going to be compatible with my Linux system.


Is there any drivers that i need to install to make it compatible?:P

Ubuntu supports ntfs just fine out of the box.  I've been using an ntfs partition for shared data on my dual-boot system for over a year now with no problems (other than the obvious bits about ntfs not being able to handle Linux-style file permissions, and Linux not being able to handle journaling on ntfs).

---

### Post by qjmoss on 2009-04-27
And ntfs doesnt limit my dl's to 4 gigs right?

---

### Post by damoxc on 2009-04-28
Yup, NTFS supports up to 16EiB.

---

### Post by qjmoss on 2009-04-29
Still getting an Input/output error.

and I updated to 9.04


everything seemed to be working fine.

---

### Post by Rocket2DMn on 2009-04-29
Please post your "dmesg" output again.  It is quite possible that this is a hardware failure.

---

### Post by qjmoss on 2009-04-29
Okay here is the output for dmseg

```
[    0.690519] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.690527] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.690533] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.690543] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.690547] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.690554] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.690560] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.690570] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:06
[    0.690574] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    0.690582] pci 0000:00:1c.2:   MEM window: 0xfa000000-0xfbffffff
[    0.690588] pci 0000:00:1c.2:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.690600] pci 0000:08:03.0: CardBus bridge, secondary bus 0000:09
[    0.690603] pci 0000:08:03.0:   IO window: 0x005000-0x0050ff
[    0.690609] pci 0000:08:03.0:   IO window: 0x005400-0x0054ff
[    0.690616] pci 0000:08:03.0:   PREFETCH window: 0x50000000-0x53ffffff
[    0.690623] pci 0000:08:03.0:   MEM window: 0x58000000-0x5bffffff
[    0.690629] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    0.690633] pci 0000:00:1e.0:   IO window: 0x5000-0x5fff
[    0.690641] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
[    0.690647] pci 0000:00:1e.0:   PREFETCH window: 0x00000050000000-0x00000053ffffff
[    0.690669] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.690676] pci 0000:00:1c.0: setting latency timer to 64
[    0.690688] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.690695] pci 0000:00:1c.1: setting latency timer to 64
[    0.690706] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.690712] pci 0000:00:1c.2: setting latency timer to 64
[    0.690722] pci 0000:00:1e.0: setting latency timer to 64
[    0.690734] pci 0000:08:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.690742] bus: 00 index 0 io port: [0x00-0xffff]
[    0.690744] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.690747] bus: 02 index 0 io port: [0x2000-0x2fff]
[    0.690749] bus: 02 index 1 mmio: [0xf6000000-0xf7ffffff]
[    0.690752] bus: 02 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.690754] bus: 02 index 3 mmio: [0x0-0x0]
[    0.690757] bus: 04 index 0 io port: [0x3000-0x3fff]
[    0.690759] bus: 04 index 1 mmio: [0xf8000000-0xf9ffffff]
[    0.690762] bus: 04 index 2 mmio: [0xf2000000-0xf3ffffff]
[    0.690764] bus: 04 index 3 mmio: [0x0-0x0]
[    0.690766] bus: 06 index 0 io port: [0x4000-0x4fff]
[    0.690769] bus: 06 index 1 mmio: [0xfa000000-0xfbffffff]
[    0.690771] bus: 06 index 2 mmio: [0xf4000000-0xf5ffffff]
[    0.690774] bus: 06 index 3 mmio: [0x0-0x0]
[    0.690776] bus: 08 index 0 io port: [0x5000-0x5fff]
[    0.690779] bus: 08 index 1 mmio: [0xfc200000-0xfc2fffff]
[    0.690781] bus: 08 index 2 mmio: [0x50000000-0x53ffffff]
[    0.690783] bus: 08 index 3 io port: [0x00-0xffff]
[    0.690786] bus: 08 index 4 mmio: [0x000000-0xffffffff]
[    0.690788] bus: 09 index 0 io port: [0x5000-0x50ff]
[    0.690791] bus: 09 index 1 io port: [0x5400-0x54ff]
[    0.690793] bus: 09 index 2 mmio: [0x50000000-0x53ffffff]
[    0.690796] bus: 09 index 3 mmio: [0x58000000-0x5bffffff]
[    0.690807] NET: Registered protocol family 2
[    0.701062] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.701370] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.701878] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.702258] TCP: Hash tables configured (established 131072 bind 65536)
[    0.702262] TCP reno registered
[    0.705137] NET: Registered protocol family 1
[    0.705296] checking if image is initramfs... it is
[    1.457912] Freeing initrd memory: 7367k freed
[    1.457962] Simple Boot Flag at 0x36 set to 0x1
[    1.458167] cpufreq: No nForce2 chipset.
[    1.458334] audit: initializing netlink socket (disabled)
[    1.458354] type=2000 audit(1241029174.456:1): initialized
[    1.467039] highmem bounce pool size: 64 pages
[    1.467046] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.468640] VFS: Disk quotas dquot_6.5.1
[    1.468712] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.469446] fuse init (API version 7.10)
[    1.469549] msgmni has been set to 1724
[    1.469757] alg: No test for stdrng (krng)
[    1.469770] io scheduler noop registered
[    1.469772] io scheduler anticipatory registered
[    1.469775] io scheduler deadline registered
[    1.469793] io scheduler cfq registered (default)
[    1.469807] pci 0000:00:02.0: Boot video device
[    1.486346] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.486407] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.486450] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.486469] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.486488] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.486506] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.486594] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.486652] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.486691] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.486710] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.486725] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.486739] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.486831] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.486890] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.486929] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.486948] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.486963] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.486978] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.487075] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.488639] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.489972] ACPI: AC Adapter [ADP1] (on-line)
[    1.507286] ACPI: EC: GPE storm detected, transactions will use polling mode
[    2.005006] ACPI: EC: missing confirmations, switch off interrupt mode.
[    2.029749] ACPI: Battery Slot [BAT0] (battery present)
[    2.029836] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    2.031374] ACPI: Lid Switch [LID0]
[    2.031430] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.031440] ACPI: Power Button (CM) [PWRB]
[    2.035558] ACPI: SSDT 3F6D8C94, 025F (r1   Sony     VAIO 20071023 PTL  20050624)
[    2.036061] ACPI: SSDT 3F6D874B, 04B7 (r1   Sony     VAIO 20071023 PTL  20050624)
[    2.039234] Monitor-Mwait will be used to enter C-1 state
[    2.039238] Monitor-Mwait will be used to enter C-2 state
[    2.039242] Monitor-Mwait will be used to enter C-3 state
[    2.039258] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.039289] processor ACPI_CPU:00: registered as cooling_device0
[    2.039294] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.039847] ACPI: SSDT 3F6D8EF3, 00E4 (r1   Sony     VAIO 20071023 PTL  20050624)
[    2.040319] ACPI: SSDT 3F6D8C02, 0092 (r1   Sony     VAIO 20071023 PTL  20050624)
[    2.041845] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.041870] processor ACPI_CPU:01: registered as cooling_device1
[    2.041875] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.065793] thermal LNXTHERM:01: registered as thermal_zone0
[    2.068675] ACPI: Thermal Zone [TZ00] (64 C)
[    2.070576] thermal LNXTHERM:02: registered as thermal_zone1
[    2.073499] ACPI: Thermal Zone [TZ01] (64 C)
[    2.073566] isapnp: Scanning for PnP cards...
[    2.427642] isapnp: No Plug & Play device found
[    2.433305] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.434527] brd: module loaded
[    2.434894] loop: module loaded
[    2.434980] Fixed MDIO Bus: probed
[    2.434986] PPP generic driver version 2.4.2
[    2.435055] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.435096] Driver 'sd' needs updating - please use bus_type methods
[    2.435107] Driver 'sr' needs updating - please use bus_type methods
[    2.435155] ahci 0000:00:1f.2: version 3.0
[    2.435176] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.435227] ahci 0000:00:1f.2: irq 2300 for MSI/MSI-X
[    2.435303] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x1 impl SATA mode
[    2.435307] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[    2.435314] ahci 0000:00:1f.2: setting latency timer to 64
[    2.435466] scsi0 : ahci
[    2.435580] scsi1 : ahci
[    2.435652] scsi2 : ahci
[    2.435732] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 2300
[    2.435735] ata2: DUMMY
[    2.435736] ata3: DUMMY
[    2.752027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.752931] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[    2.752934] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.753273] ata1.00: ATA-8: FUJITSU MHY2160BH, 0000000B, max UDMA/100
[    2.753277] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.754255] ata1.00: ACPI cmd ef/90:03:00:00:00:a0 succeeded
[    2.754258] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.754627] ata1.00: configured for UDMA/100
[    2.768152] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2160B 0000 PQ: 0 ANSI: 5
[    2.768269] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.768289] sd 0:0:0:0: [sda] Write Protect is off
[    2.768292] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.768322] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.768401] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    2.768419] sd 0:0:0:0: [sda] Write Protect is off
[    2.768421] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.768451] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.768455]  sda: sda1 sda2 < sda5 >
[    2.812553] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.812614] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.812678] ata_piix 0000:00:1f.1: version 2.12
[    2.812689] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.812734] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.812829] scsi3 : ata_piix
[    2.812902] scsi4 : ata_piix
[    2.813885] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.813888] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.976507] ata4.00: ATAPI: Optiarc DVD RW AD-7560A, DS02, max UDMA/33
[    2.992437] ata4.00: configured for UDMA/33
[    3.160230] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DS02 PQ: 0 ANSI: 5
[    3.165371] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.165375] Uniform CD-ROM driver Revision: 3.20
[    3.165497] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.165549] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.166354] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.166378] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.166401] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.166405] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.166481] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.170388] ehci_hcd 0000:00:1a.7: debug port 1
[    3.170396] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.170417] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
[    3.184014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.184088] usb usb1: configuration #1 chosen from 1 choice
[    3.184122] hub 1-0:1.0: USB hub found
[    3.184131] hub 1-0:1.0: 4 ports detected
[    3.184255] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.184270] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.184274] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.184322] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.188237] ehci_hcd 0000:00:1d.7: debug port 1
[    3.188245] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.188261] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
[    3.204012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.204084] usb usb2: configuration #1 chosen from 1 choice
[    3.204116] hub 2-0:1.0: USB hub found
[    3.204124] hub 2-0:1.0: 6 ports detected
[    3.204239] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.204261] uhci_hcd: USB Universal Host Controller Interface driver
[    3.204295] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.204303] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.204307] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.204356] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.204396] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    3.204482] usb usb3: configuration #1 chosen from 1 choice
[    3.204515] hub 3-0:1.0: USB hub found
[    3.204522] hub 3-0:1.0: 2 ports detected
[    3.204624] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.204631] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.204635] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.204690] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.204728] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    3.204816] usb usb4: configuration #1 chosen from 1 choice
[    3.204847] hub 4-0:1.0: USB hub found
[    3.204855] hub 4-0:1.0: 2 ports detected
[    3.204955] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.204962] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.204966] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.205017] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.205045] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    3.205129] usb usb5: configuration #1 chosen from 1 choice
[    3.205159] hub 5-0:1.0: USB hub found
[    3.205166] hub 5-0:1.0: 2 ports detected
[    3.205268] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.205275] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.205279] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.205334] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.205374] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.205472] usb usb6: configuration #1 chosen from 1 choice
[    3.205505] hub 6-0:1.0: USB hub found
[    3.205513] hub 6-0:1.0: 2 ports detected
[    3.205610] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.205617] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.205621] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.205673] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.205703] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.205793] usb usb7: configuration #1 chosen from 1 choice
[    3.205822] hub 7-0:1.0: USB hub found
[    3.205829] hub 7-0:1.0: 2 ports detected
[    3.205978] usbcore: registered new interface driver libusual
[    3.206017] usbcore: registered new interface driver usbserial
[    3.206029] USB Serial support registered for generic
[    3.206049] usbcore: registered new interface driver usbserial_generic
[    3.206051] usbserial: USB Serial Driver core
[    3.206108] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.210085] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.213492] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.213498] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.213502] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.213505] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.213507] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.216049] mice: PS/2 mouse device common for all mice
[    3.228081] rtc_cmos 00:07: RTC can wake from S4
[    3.228120] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    3.228156] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    3.228234] device-mapper: uevent: version 1.0.3
[    3.228343] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.228428] device-mapper: multipath: version 1.0.5 loaded
[    3.228431] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.228525] EISA: Probing bus 0 at eisa.0
[    3.228533] Cannot allocate resource for EISA slot 1
[    3.228537] Cannot allocate resource for EISA slot 2
[    3.228539] Cannot allocate resource for EISA slot 3
[    3.228542] Cannot allocate resource for EISA slot 4
[    3.228545] Cannot allocate resource for EISA slot 5
[    3.228562] EISA: Detected 0 cards.
[    3.228707] cpuidle: using governor ladder
[    3.228851] cpuidle: using governor menu
[    3.229466] TCP cubic registered
[    3.229586] NET: Registered protocol family 10
[    3.230097] lo: Disabled Privacy Extensions
[    3.230503] NET: Registered protocol family 17
[    3.230524] Bluetooth: L2CAP ver 2.11
[    3.230526] Bluetooth: L2CAP socket layer initialized
[    3.230529] Bluetooth: SCO (Voice Link) ver 0.6
[    3.230531] Bluetooth: SCO socket layer initialized
[    3.230572] Bluetooth: RFCOMM socket layer initialized
[    3.230581] Bluetooth: RFCOMM TTY layer initialized
[    3.230583] Bluetooth: RFCOMM ver 1.10
[    3.230632] Marking TSC unstable due to TSC halts in idle
[    3.231627] Using IPI No-Shortcut mode
[    3.231721] registered taskstats version 1
[    3.231876]   Magic number: 5:348:343
[    3.231902] tty tty60: hash matches
[    3.231982] rtc_cmos 00:07: setting system clock to 2009-04-29 18:19:36 UTC (1241029176)
[    3.231985] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.231987] EDD information not available.
[    3.232319] Freeing unused kernel memory: 532k freed
[    3.232503] Write protecting the kernel text: 4128k
[    3.232572] Write protecting the kernel read-only data: 1532k
[    3.431726] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.485660] sky2 driver version 1.22
[    3.485723] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.485745] sky2 0000:02:00.0: setting latency timer to 64
[    3.485808] sky2 0000:02:00.0: Yukon-2 FE chip revision 3
[    3.549814] sky2 0000:02:00.0: Marvell Yukon 88E8039 Fast Ethernet Controller
[    3.549818]  Part Number: Yukon 88E8039
[    3.549820]  Engineering Level: Rev. 1.5
[    3.549822]  Manufacturer: Marvell
[    3.549999] sky2 0000:02:00.0: irq 2299 for MSI/MSI-X
[    3.573040] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    3.599361] sky2 eth0: addr 00:1a:80:26:28:81
[    3.648134] ohci1394 0000:08:03.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.697961] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.718139] usb 2-4: configuration #1 chosen from 1 choice
[    3.734864] Initializing USB Mass Storage driver...
[    3.753976] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.757185] usbcore: registered new interface driver usb-storage
[    3.757190] USB Mass Storage support registered.
[    3.758391] usb-storage: device found at 3
[    3.758395] usb-storage: waiting for device to settle before scanning
[    3.976064] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    4.017035] PM: Starting manual resume from disk
[    4.017039] PM: Resume from partition 8:5
[    4.017041] PM: Checking hibernation image.
[    4.017259] PM: Resume from disk failed.
[    4.022073] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.022076] EXT3-fs: write access will be enabled during recovery.
[    4.158542] usb 6-1: configuration #1 chosen from 1 choice
[    4.167495] usbcore: registered new interface driver hiddev
[    4.219218] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input4
[    4.228111] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:1d.1-1/input0
[    4.228134] usbcore: registered new interface driver usbhid
[    4.228138] usbhid: v2.6:USB HID core driver
[    5.009085] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030282ed1b]
[    7.019737] kjournald starting.  Commit interval 5 seconds
[    7.019761] EXT3-fs: recovery complete.
[    7.020545] EXT3-fs: mounted filesystem with ordered data mode.
[    8.756349] usb-storage: device scan complete
[    8.756996] scsi 5:0:0:0: Direct-Access     WD       10EAVS External  1.75 PQ: 0 ANSI: 4
[    8.758255] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    8.758877] sd 5:0:0:0: [sdb] Write Protect is off
[    8.758880] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    8.758883] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    8.759729] sd 5:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    8.760375] sd 5:0:0:0: [sdb] Write Protect is off
[    8.760378] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    8.760381] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[    8.760384]  sdb: sdb1
[    8.772863] sd 5:0:0:0: [sdb] Attached SCSI disk
[    8.772933] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   12.734213] udev: starting version 141
[   12.885381] Linux agpgart interface v0.103
[   12.915361] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   12.915899] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[   12.919546] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   12.947225] sony-laptop: Sony Notebook Control Driver v0.6.
[   12.949120] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/SNY5001:00/input/input5
[   12.976354] input: Sony Vaio Jogdial as /devices/virtual/input/input6
[   12.982940] acpi device:07: registered as cooling_device2
[   12.983471] acpi device:09: registered as cooling_device3
[   12.983728] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05/input/input7
[   13.009207] sony-laptop: brightness ignored, must be controlled by ACPI video driver
[   13.009214] sony-laptop: detected Sony Vaio N Series
[   13.049209] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.049331] cfg80211: Calling CRDA to update world regulatory domain
[   13.089781] iTCO_vendor_support: vendor-support=0
[   13.092411] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.092704] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   13.092816] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.226102] yenta_cardbus 0000:08:03.0: CardBus bridge found [104d:902d]
[   13.226129] yenta_cardbus 0000:08:03.0: Enabling burst memory read transactions
[   13.226136] yenta_cardbus 0000:08:03.0: Using CSCINT to route CSC interrupts to PCI
[   13.226139] yenta_cardbus 0000:08:03.0: Routing CardBus interrupts to PCI
[   13.226146] yenta_cardbus 0000:08:03.0: TI: mfunc 0x01121b22, devctl 0x64
[   13.255830] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.437640] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.457460] yenta_cardbus 0000:08:03.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   13.457466] yenta_cardbus 0000:08:03.0: Socket status: 30000006
[   13.457470] pci_bus 0000:08: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   13.457479] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   13.457483] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: clean.
[   13.457798] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   13.457801] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   13.458381] tifm_7xx1 0000:08:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.515093] cfg80211: World regulatory domain updated:
[   13.515098] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.515101] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.515104] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.515107] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.515110] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.515112] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.783330] ath5k_pci 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   13.783347] ath5k_pci 0000:06:00.0: setting latency timer to 64
[   13.783433] ath5k_pci 0000:06:00.0: registered as 'phy0'
[   13.826571] phy0: Selected rate control algorithm 'pid'
[   13.926790] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   13.928996] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.929927] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   13.930681] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   13.931643] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   13.954391] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   14.022632] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input9
[   14.040303] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.040410] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.043361] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input10
[   14.071338] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   14.362871] lp: driver loaded but no devices found
[   14.487869] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k
[   14.501050] Clocksource tsc unstable (delta = -100599764 ns)
[   15.037174] EXT3 FS on sda1, internal journal
[   16.022173] type=1505 audit(1241029189.288:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2178
[   16.079210] type=1505 audit(1241029189.345:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2182
[   16.079362] type=1505 audit(1241029189.345:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2182
[   16.079415] type=1505 audit(1241029189.345:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2182
[   16.079463] type=1505 audit(1241029189.345:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2182
[   16.238477] type=1505 audit(1241029189.505:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2187
[   16.238691] type=1505 audit(1241029189.505:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2187
[   16.272890] type=1505 audit(1241029189.537:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2191
[   18.912045] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.912050] Bluetooth: BNEP filters: protocol multicast
[   18.932003] Bridge firewalling registered
[   20.201047] ppdev: user-space parallel port driver
[   21.143548] [drm] Initialized drm 1.1.0 20060810
[   21.150312] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.150319] pci 0000:00:02.0: setting latency timer to 64
[   21.150452] pci 0000:00:02.0: irq 2298 for MSI/MSI-X
[   21.150564] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   21.157872] [drm:i915_setparam] *ERROR* unknown parameter 4
[   23.735478] sky2 eth0: enabling interface
[   23.735724] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.765610] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.709449] wlan0: authenticate with AP 00:1c:df:d7:ba:af
[   25.710935] wlan0: authenticated
[   25.710939] wlan0: associate with AP 00:1c:df:d7:ba:af
[   25.713220] wlan0: RX AssocResp from 00:1c:df:d7:ba:af (capab=0x421 status=0 aid=1)
[   25.713224] wlan0: associated
[   25.713880] wlan0: disassociating by local choice (reason=3)
[   42.029170] wlan0: authenticate with AP 00:1c:df:d7:ba:af
[   42.030628] wlan0: authenticated
[   42.030632] wlan0: associate with AP 00:1c:df:d7:ba:af
[   42.032819] wlan0: RX ReassocResp from 00:1c:df:d7:ba:af (capab=0x421 status=0 aid=1)
[   42.032822] wlan0: associated
[   42.033146] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   52.876072] wlan0: no IPv6 routers present

```


But with the days, i've noticed, that with these errors, it happens right when my external unmounts.


my external unmounts randomly.

and i can't install the windows software for my external because wine wont open..

power saving feature?




And here is something i've though could be the problem.. tell me if this isnt right
[IMG]http://i43.tinypic.com/1grhw0.png[/IMG]

---

### Post by qjmoss on 2009-04-29
And here is a photo of my torrent's going steady...

and all of a sudden, my external unmounts, then i have to force recheck and it starts again

[IMG]http://i42.tinypic.com/2edoaxk.png[/IMG]

---

### Post by Rocket2DMn on 2009-04-29
If the drive is randomly unmounting itself, you need to file a bug report.  It is possible that this is a power saving feature that Ubuntu hasn't recognized yet.  If the Input/Output error is coming from Deluge, then I would think that this is the problem, though I don't know why the drive would unmount itself when it's active.

---

