---
title: "Help with linux"
date: 2009-03-31
forum: General Help
---

### Post by CJ1985 on 2009-03-31
Hello, I'm looking to get some help. I am very very new to linux. I know some things, and don't know other things.

I ran the following command:

```
ps -ef | grep <userid> | more
```

And it came up with a bunch of tasks, but what one is technically the task id? And which one would technically be the owner? I'm assuming me, but then there is also a root in there as well. So I'm a little confused on that one. The command above comes out with something like this:

```
<userid>  23862     1  0 Mar10 ?        00:00:00 vim blob.txt
root     13846  3512  0 20:52 ?        00:00:00 sshd: <userid> [priv]
```

---

### Post by 3Miro on 2009-03-31
grep command gives you all the lines that contain the grep pattern (i.e.```
 ps -e | grep me 
``` would return all processes owned by user me as well as gnoME processes and everything having "me" in its string. To select specific process, you have to do more coding looking for specific thing in specific places.

So basically
```
 ps -ef | grep me 
``` gets all the output of ps -ef command and gives it to grep which then selects the lines that contain "me" and displays them. (more is simply a way to handle long outputs by letting you scroll down slowly, less is a better command, it gives you more options).

---

### Post by CJ1985 on 2009-03-31
Yes, I understand that much. But how do I know which one is the task id? and which one is the owner of that task?

---

### Post by Vaphell on 2009-03-31
when you run ps -ef process id is in the column labeled PID
in your example 2nd one

owner is of course in the first column, but your grep found userid in process name and listed that process owned by root too (grep finds lines with a given pattern).

you can achieve proper effect by using proper parameters for ps command

i use ps ux to list my processes
ps -fU userid shows processes owned by userid
ps --help to learn more, you can make combos of these switches

---

### Post by CJ1985 on 2009-03-31
Okay, thank you!

---

### Post by CJ1985 on 2009-03-31
Also, I just wanted to add, this is what I get when I enter the command

```
$ ps -ef | grep <userid> | more
<userid>  23862     1  0 Mar10 ?        00:00:00 vim blob.txt
root     14729  3512  0 21:16 ?        00:00:00 sshd: <userid> [priv]
<userid>  14731 14729  0 21:16 ?        00:00:00 sshd: <userid>@notty
<userid>  14732 14731  0 21:16 ?        00:00:00 /usr/libexec/openssh/sftp-server
root     15134  3512  0 21:35 ?        00:00:00 sshd: <userid> [priv]
<userid>  15136 15134  0 21:35 ?        00:00:00 sshd: <userid>@pts/24
<userid>  15137 15136  0 21:35 pts/24   00:00:00 -bash
<userid>  15198 15137  0 21:37 pts/24   00:00:00 ps -ef
<userid>  15199 15137  0 21:37 pts/24   00:00:00 grep <userid>
<userid>  15200 15137  0 21:37 pts/24   00:00:00 more
```

So what would be the task name that corresponds to PID 1?

---

### Post by CJ1985 on 2009-03-31
Oops, I asked that wrong and I don't see a edit button to edit the post. What I meant to say, what coloumn would be the task name? Would it be the last column, like for example vim blob.txt, would that be a task name?

---

### Post by hyper_ch on 2009-04-01
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by CJ1985 on 2009-04-01
Alright, sorry about that hyper_ch. I'm new here, so I didn't know and I definitely apologize. I changed all the titles to each posts I made to what I believe is the correct way to do it. I don't know if it will show up on board as that though.

----

I am still trying to work this out. What the task name is that corresponds to PID 1, and who the owner of it is below and would it be task id as init [3] and owner would be root?

```
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0  2008 ?        00:04:47 init [3]
root         2     1  0  2008 ?        00:00:06 [migrati
root         3     1  0  2008 ?        00:00:00 [ksoftir
root         4     1  0  2008 ?        00:00:02 [migrati
root         5     1  0  2008 ?        00:00:00 [ksoftir
root         6     1  0  2008 ?        00:00:06 [migrati
root         7     1  0  2008 ?        00:00:00 [ksoftir
root         8     1  0  2008 ?        00:00:02 [migrati
root         9     1  0  2008 ?        00:00:00 [ksoftir
root        10     1  0  2008 ?        00:00:00 [events/
root        11     1  0  2008 ?        00:00:01 [events/
root        12     1  0  2008 ?        00:00:00 [events/
root        13     1  0  2008 ?        00:00:00 [events/
root        14    10  0  2008 ?        00:00:00 [khelper
root        15    10  0  2008 ?        00:00:00 [kacpid]
root        54    10  0  2008 ?        00:00:00 [kblockd
root        55    10  0  2008 ?        00:00:00 [kblockd
root        56    10  0  2008 ?        00:00:00 [kblockd
root        57    10  0  2008 ?        00:00:00 [kblockd
root        70    10  0  2008 ?        00:00:00 [aio/0]
root        71    10  0  2008 ?        00:00:00 [aio/1]
root        72    10  0  2008 ?        00:00:00 [aio/2]
root        73    10  0  2008 ?        00:00:00 [aio/3]
root        58     1  0  2008 ?        00:00:00 [khubd]
root        69     1  0  2008 ?        04:37:38 [kswapd0
root       146     1  0  2008 ?        00:00:00 [kseriod
root       228     1  0  2008 ?        00:00:00 [scsi_eh
root       229     1  0  2008 ?        00:00:00 [ahc_dv_
root       237     1  0  2008 ?        00:00:00 [scsi_eh
root       238     1  0  2008 ?        00:00:00 [ahc_dv_
root       250     1  0  2008 ?        00:00:00 [scsi_eh
root       279     1  0  2008 ?        00:00:00 [scsi_eh
root       280     1  0  2008 ?        00:00:00 [qla2300
root       288     1  0  2008 ?        00:00:00 [scsi_eh
root       289     1  0  2008 ?        00:00:00 [qla2300
root       313     1  0  2008 ?        00:02:35 [kjourna
root      1673     1  0  2008 ?        00:00:00 udevd
root      1728     1  0  2008 ?        00:00:00 [shpchpd
root      2262    13  0  2008 ?        00:00:00 [kauditd
root      2348     1  0  2008 ?        00:00:00 [emcpd]
root      2349     1  0  2008 ?        00:02:26 [emcpdef
root      2386     1  0  2008 ?        00:00:00 [MpAsync
root      2387     1  0  2008 ?        00:00:00 [MpTestD
root      2388     1  0  2008 ?        00:00:00 [MpPirpN
root      2389     1  0  2008 ?        00:00:00 [MpPerio
root      2390     1  0  2008 ?        00:00:00 [MpDefer
root      2391     1  0  2008 ?        00:00:00 [MpGener
root      2392     1  0  2008 ?        00:00:00 [MpcAsyn
root      2393     1  0  2008 ?        00:00:00 [MpcResu
root      2394     1  0  2008 ?        00:00:27 [MpcPeri
root      2395     1  0  2008 ?        00:00:00 [MpcGrDa
root      2396     1  0  2008 ?        00:00:00 [MpcDisp
root      2397     1  0  2008 ?        00:00:00 [MpcTest
root      2398     1  0  2008 ?        00:00:00 [MpaaAsy
root      2402     1  0  2008 ?        00:00:00 [MpaaDef
root      2403     1  0  2008 ?        00:00:00 [MpaaGen
root      2404     1  0  2008 ?        00:00:00 [MpapAsy
root      2401     1  0  2008 ?        00:00:00 [MpaaPer
root      2399     1  0  2008 ?        00:00:00 [MpaaTes
root      2400     1  0  2008 ?        00:00:00 [MpaaPir
root      2405     1  0  2008 ?        00:00:00 [MpapRes
root      2406     1  0  2008 ?        00:00:00 [MpapPer
root      2407     1  0  2008 ?        00:00:00 [MpapGrD
root      2408     1  0  2008 ?        00:00:00 [MpapDis
root      2409     1  0  2008 ?        00:00:00 [MpapTes
root      2430     1  0  2008 ?        00:00:00 [MpcTest
root      2606    10  0  2008 ?        00:00:00 [kmirror
root      2607    10  0  2008 ?        00:00:00 [kmir_mo
root      2631     1  0  2008 ?        00:00:00 [kjourna
root      2632     1  0  2008 ?        00:06:47 [kjourna
root      2633     1  0  2008 ?        00:01:05 [kjourna
root      2634     1  0  2008 ?        00:03:01 [kjourna
root      2635     1  0  2008 ?        00:02:41 [kjourna
root      3247     1  0  2008 ?        00:03:50 syslogd 
root      3251     1  0  2008 ?        00:01:36 klogd -x
root      3262     1  0  2008 ?        00:04:26 irqbalan
rpc       3281     1  0  2008 ?        00:00:00 portmap
rpcuser   3301     1  0  2008 ?        00:00:00 rpc.stat
root      3333     1  0  2008 ?        00:02:37 rpc.idma
root      3360     1  0  2008 ?        00:05:13 /opt/Nav
root      3452     1  0  2008 ?        00:00:00 /usr/sbi
root      3460     1  0  2008 ?        00:07:41 /usr/loc
root      3476     1  0  2008 ?        00:00:05 /usr/sbi
root      3512     1  0  2008 ?        00:05:33 /usr/sbi
root      3533     1  0  2008 ?        00:00:00 xinetd -
root      3552     1  0  2008 ?        00:05:44 sendmail
smmsp     3560     1  0  2008 ?        00:00:29 sendmail
root      3572     1  0  2008 ?        00:01:26 /usr/sbi
root      3582     1  0  2008 ?        00:02:34 crond
xfs       3613     1  0  2008 ?        00:00:09 xfs -dro
root      3632     1  0  2008 ?        00:01:33 /usr/sbi
dbus      3642     1  0  2008 ?        00:00:00 dbus-dae
root      3656     1  0  2008 ?        00:36:29 hald
root      4204     1  0  2008 tty2     00:00:00 /sbin/mi
root      4205     1  0  2008 tty3     00:00:00 /sbin/mi
root      4206     1  0  2008 tty4     00:00:00 /sbin/mi
root      4207     1  0  2008 tty5     00:00:00 /sbin/mi
root      4208     1  0  2008 tty6     00:00:00 /sbin/mi
sladd03  29356     1  0 Jan29 ?        00:00:00 vim prac
jbell05  32695     1  0 Feb02 ?        00:00:00 ssh-agen
cspenc02 18676     1  0 Feb03 ?        00:00:00 vim
root      4192     1  0 Feb05 tty1     00:00:00 /sbin/mi
root     32407  3512  0 Feb24 ?        00:00:00 sshd: dv
sshd     32408 32407  0 Feb24 ?        00:00:00 [sshd] <
dbedel01 16569     1  0 Mar06 ?        00:00:00 vim addr
cbond03  23862     1  0 Mar10 ?        00:00:00 vim blob
cellis04 12749     1  0 Mar11 ?        00:00:00 vim addr
root     22868    11  0 Mar17 ?        00:00:04 [pdflush
root     23239    10  0 Mar17 ?        00:00:21 [pdflush
root     30182     1  0 Mar17 ?        00:00:00 /bin/sh 
mysql    30221 30182  0 Mar17 ?        00:29:15 /usr/sbi
drobin11 23430     1  0 Mar21 ?        00:00:00 vim colo
drobin11 24448     1  0 Mar21 ?        00:00:00 vim colo
drobin11 25055     1  0 Mar21 ?        00:00:00 vim phme
dhood02  31769     1  0 Mar23 ?        00:00:00 vim mysu
dhood02  32221     1  0 Mar23 ?        00:00:00 vim mysu
root     10943  3512  0 Mar28 ?        00:00:00 sshd: kd
kdelas01 10965 10943  0 Mar28 ?        00:00:00 sshd: kd
kdelas01 10966 10965  0 Mar28 pts/18   00:00:00 -bash
root     11103  3512  0 Mar28 ?        00:00:00 sshd: kd
kdelas01 11105 11103  0 Mar28 ?        00:00:00 sshd: kd
kdelas01 11106 11105  0 Mar28 pts/14   00:00:00 -bash
bcoome01 14437     1  0 Mar30 ?        00:00:00 vim docu
apache    9058  3572  0 Mar31 ?        00:00:02 /usr/sbi
root     11877  3512  0 Mar31 ?        00:00:00 sshd: kk
kkavan01 11881 11877  0 Mar31 ?        00:00:00 sshd: kk
kkavan01 11882 11881  0 Mar31 ?        00:00:04 /usr/lib
root     12431  3512  0 Mar31 ?        00:00:00 sshd: rl
rleona01 12433 12431  0 Mar31 ?        00:00:00 sshd: rl
rleona01 12434 12433  0 Mar31 ?        00:00:00 /usr/lib
root     14857  3512  0 Mar31 ?        00:00:00 sshd: kk
kkavan01 14859 14857  0 Mar31 ?        00:00:00 sshd: kk
kkavan01 14860 14859  0 Mar31 pts/21   00:00:00 -bash
root     16344  3512  0 Mar31 ?        00:00:00 sshd: as
astone06 16346 16344  0 Mar31 ?        00:00:00 sshd: as
astone06 16347 16346  0 Mar31 pts/15   00:00:00 -bash
apache   18251  3572  0 Mar31 ?        00:00:03 /usr/sbi
apache   18277  3572  0 Mar31 ?        00:00:02 /usr/sbi
apache   18384  3572  0 Mar31 ?        00:00:02 /usr/sbi
apache   18601  3572  0 Mar31 ?        00:00:02 /usr/sbi
root     18762  3512  0 Mar31 ?        00:00:00 sshd: st
stellg01 18764 18762  0 Mar31 ?        00:00:01 sshd: st
stellg01 18765 18764  0 Mar31 ?        00:00:02 /usr/lib
root     22666  3512  0 03:14 ?        00:00:00 sshd: nh
nhanso01 22668 22666  0 03:14 ?        00:00:00 sshd: nh
nhanso01 22669 22668  0 03:15 ?        00:00:00 /usr/lib
apache   24252  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24253  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24254  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24255  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24256  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24257  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24258  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24259  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24260  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24261  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24262  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24263  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24264  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24265  3572  0 04:56 ?        00:00:00 /usr/sbi
apache   24266  3572  0 04:56 ?        00:00:00 /usr/sbi
root     24501  3512  0 05:18 ?        00:00:00 sshd: bf
bfishe03 24503 24501  0 05:18 ?        00:00:00 sshd: bf
bfishe03 24504 24503  0 05:18 ?        00:00:00 /usr/lib
root     24541  3512  0 05:20 ?        00:00:00 sshd: bf
bfishe03 24543 24541  0 05:20 ?        00:00:00 sshd: bf
bfishe03 24544 24543  0 05:20 ?        00:00:00 /usr/lib
root     24561  3512  0 05:20 ?        00:00:00 sshd: rz
rzapat01 24563 24561  0 05:20 ?        00:00:00 sshd: rz
rzapat01 24564 24563  0 05:20 ?        00:00:01 /usr/lib
root     24848  3512  0 05:46 ?        00:00:00 sshd: cb
cbond03  24850 24848  0 05:46 ?        00:00:00 sshd: cb
cbond03  24851 24850  0 05:46 pts/0    00:00:00 -bash
root     24914  3552  0 05:51 ?        00:00:00 sendmail
root     24938  3512  0 05:55 ?        00:00:00 sshd: rz
rzapat01 24940 24938  0 05:55 ?        00:00:00 sshd: rz
rzapat01 24941 24940  0 05:55 ?        00:00:00 /usr/lib
cbond03  24960 24851  0 05:55 pts/0    00:00:00 ps -ef
```

And wouldn't the userid sshd be the second most # of tasks being ran? Or it would be root? I'm so confused! Please help... :(

---

### Post by Vaphell on 2009-04-01
hmm, your questions are convoluted :-)

these are all processes
first column: owner
second: process id (integer number)
3rd: parent id?
... some crap :P
last column: command used to create the process (effectively it would be process' description you'd get in gui process monitor)

these with low id (0,1) are probably the core system ones, responsible for running others. Thats why so many processes has them as their parent (i guess PPID = Parent Process Id?)
so when you get to the users session, some root process has to spawn new one for the user. And this is where user's processes begin.

---

