---
title: "network not working to potential!"
date: 2005-12-20
forum: Desktop Environments
---

### Post by dirtbag on 2005-12-20
Putting files on my ubuntu server using samba, or taking them off, I can only manage to get 2.1 megabytes per second (both ways). Regardless if its through a switch, or a cross over cable. Between two xp boxes its peaking about 10-11 megabytes per second.

I have looked around for a while for information on the problem, as a friend also has the problem so i thought it would be widespread, but maybe not!?

Any help would be much appreciated

---

### Post by Ocxic on 2005-12-20
you;ll never get a network to run at a true 100mb/s 10mb/s speed, even though it says it capable of it. it just the way it works, i've never seen anyone able to do what your asking.  10-11 mb/s is fast, there is now reall need to transfer anyhting faster then that, or get gigabit ethernet cards, they will run faster tho it still won't run close to 100 mb/s.

---

### Post by alamba on 2005-12-21
That's ocxic, but there's not reason why 2 XP boxes should deliver 10-11 mbps while 2 linux boxes deliver 2.1 mbps on the same network. 

Dirtbag: Can you post a snapshot of tethereal?

Akshay

---

### Post by dirtbag on 2005-12-21
Yea, any computer accessing the linux box gets a maximum of 2.1 megabytes per second speed regardless of if downloading or uploading to it (measured by sygate firewall)

so what do you want me to be doing when i get a snapshot of tethereal? Just downloading from the linux box?

---

### Post by dirtbag on 2005-12-21
here is the output of tethereal when i was transfering a file off the linux box.
What would be a reason behind all the tcp checksum errors? :???:  those don't seem to good @ all!

34.438546    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [PSH, ACK] Seq=116986362 Ack=224406 Win=32767 [TCP CHECKSUM INCORRECT] Len=183
 34.439160    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224406 Ack=116980522 Win=65535 Len=0
 34.439181    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224406 Ack=116983442 Win=65535 Len=0
 34.439468    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224406 Ack=116986362 Win=65535 Len=0
 34.439544    10.0.0.10 -> 10.0.0.11    SMB Read AndX Request, FID: 0x33e0, 4096 bytes at offset 205090816
 34.439699    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116986545 Ack=224469 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.439716    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116988005 Ack=224469 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.439733    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [PSH, ACK] Seq=116989465 Ack=224469 Win=32767 [TCP CHECKSUM INCORRECT] Len=1239
 34.440732    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224469 Ack=116989465 Win=65535 Len=0
 34.440891    10.0.0.10 -> 10.0.0.11    SMB Read AndX Request, FID: 0x33e0, 61440 bytes at offset 205094912
 34.441126    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116990704 Ack=224532 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.441145    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116992164 Ack=224532 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.441162    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116993624 Ack=224532 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.441203    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=116995084 Ack=224532 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.442285    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224532 Ack=116993624 Win=65535 Len=0
 34.442310    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224532 Ack=116996544 Win=65535 Len=0
 34.566188    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117244630 Ack=224910 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.566689    10.0.0.10 -> 10.0.0.11    TCP [TCP Previous segment lost] 1936 > microsoft-ds [ACK] Seq=224910 Ack=117237330 Win=65535 Len=0
 34.566710    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224910 Ack=117240250 Win=65535 Len=0
 34.567181    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224910 Ack=117243170 Win=65535 Len=0
 34.567201    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224910 Ack=117246090 Win=65535 Len=0
 34.567479    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224910 Ack=117249010 Win=65535 Len=0
 34.567545    10.0.0.10 -> 10.0.0.11    SMB Read AndX Request, FID: 0x33e0, 4096 bytes at offset 205352960
 34.569975    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117249193 Ack=224973 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.569996    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117250653 Ack=224973 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.570042    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [PSH, ACK] Seq=117252113 Ack=224973 Win=32767 [TCP CHECKSUM INCORRECT] Len=1239
 34.570947    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=224973 Ack=117252113 Win=65535 Len=0
 34.571107    10.0.0.10 -> 10.0.0.11    SMB Read AndX Request, FID: 0x33e0, 61440 bytes at offset 205357056
 34.571344    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117253352 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571363    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117254812 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571380    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117256272 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571395    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117257732 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571504    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117259192 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571623    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117260652 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571746    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117262112 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571871    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117263572 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.571995    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117265032 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.572119    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117266492 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.572240    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117267952 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.572362    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117269412 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.572498    10.0.0.11 -> 10.0.0.10    TCP [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117270872 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.572515    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117256272 Win=65535 Len=0
 34.572543    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117259192 Win=65535 Len=0
 34.572854    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117262112 Win=65535 Len=0
 34.572875    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117265032 Win=65535 Len=0
 34.573224    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117279632 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.573362    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117267952 Win=65535 Len=0
 34.573674    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117273792 Win=65535 Len=0
 34.573962    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117288392 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.574207    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117291312 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.574454    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117294232 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.574554    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117282552 Win=65535 Len=0
 34.574606    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117285472 Win=65535 Len=0
 34.574823    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117298612 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.575069    10.0.0.11 -> 10.0.0.10    TCP [TCP Previous segment lost] [Continuation to #228] microsoft-ds > 1936 [ACK] Seq=117301532 Ack=225036 Win=32767 [TCP CHECKSUM INCORRECT] Len=1460
 34.575115    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117288392 Win=65535 Len=0
 34.575134    10.0.0.10 -> 10.0.0.11    TCP 1936 > microsoft-ds [ACK] Seq=225036 Ack=117291312 Win=65535 Len=0
 34

---

### Post by toallpointswest on 2006-09-05
*Bump* As I'm having the exact same problem on Dapper

---

### Post by dirtbag on 2006-09-05
I found out the problem in the end seemed to be not the network but the motherboard IDE controller was failing... and kept on reverting to PIO mode, which is extremely slow, so the network was not being worked to its full potential because the computer could not serve up the data to send quick enough, after replacing the motherboard everything was fine.

---

### Post by toallpointswest on 2006-09-05
How did you determine your motherboard was going bad? I know my board is constantly generating:
```
Sep  4 21:44:45 localhost kernel: [17182255.752000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep  4 21:44:45 localhost kernel: [17182255.752000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Sep  4 22:24:40 localhost kernel: [17184650.624000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep  4 22:24:40 localhost kernel: [17184650.624000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Sep  4 23:31:51 localhost kernel: [17188681.372000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep  4 23:31:51 localhost kernel: [17188681.372000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Sep  5 04:28:52 localhost kernel: [17206500.784000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep  5 04:28:52 localhost kernel: [17206500.784000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Sep  5 07:35:37 localhost kernel: [17217705.176000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep  5 07:35:37 localhost kernel: [17217705.176000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }

```

Even with a new drive and cabling. However my other drives (LVM'd) are not generating any error messages.

---

### Post by dirtbag on 2006-09-05
By the looks of it, there is a problem with data being manipulated on your hard drive. This could because the IDE controller on the motherboard, or the drive. Have you had the hard drive working without the errors? Even though it is new, you could have received a dub. 

Perhaps you should start a new thread/search for those kernel errors as the problem won't get much exposure with the name "network not working to potential", and maybe throw a new thread in on the dapper section about your network problems.

---

