---
title: "/dev/hda1 100% used"
date: 2006-10-02
forum: Desktop Environments
---

### Post by zmartant on 2006-10-02
Hello,

I am a newbie!  I have been using Ubuntu for about two weeks now and its been FANTASTIC!  During login, I received a pop-up stating that /dev/hda1 is 100% used.  I really do not know what that meant so I googled.  I have somewhat an idea, but not very clear.  I do have VMWare with XP Pro running NTFS.  I am still a newbie, so please be gentle!


I did the following command df -h :
[HTML]
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   34G  228M 100% /
varrun                126M   92K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M   88K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
[/HTML]

I cd'd into /dev :
[HTML]
acpi       port   ptyd9  ptyr7  ptyv5  ptyz3    tty30  ttyb6  ttyp4  ttyS22 ttyu0  ttyxe
agpgart    ppp    ptyda  ptyr8  ptyv6  ptyz4    tty31  ttyb7  ttyp5  ttyS23  ttyu1  ttyxf
audio      psaux  ptydb  ptyr9  ptyv7  ptyz5    tty32  ttyb8  ttyp6  ttyS24  ttyu2  ttyy0
bus        ptmx   ptydc  ptyra  ptyv8  ptyz6    tty33  ttyb9  ttyp7  ttyS25  ttyu3  ttyy1
cdrom      pts    ptydd  ptyrb  ptyv9  ptyz7    tty34  ttyba  ttyp8  ttyS26  ttyu4  ttyy2
console    ptya0  ptyde  ptyrc  ptyva  ptyz8    tty35  ttybb  ttyp9  ttyS27  ttyu5  ttyy3
core       ptya1  ptydf  ptyrd  ptyvb  ptyz9    tty36  ttybc  ttypa  ttyS28  ttyu6  ttyy4
disk       ptya2  ptye0  ptyre  ptyvc  ptyza    tty37  ttybd  ttypb  ttyS29  ttyu7  ttyy5
dsp        ptya3  ptye1  ptyrf  ptyvd  ptyzb    tty38  ttybe  ttypc  ttys3   ttyu8  ttyy6
evms       ptya4  ptye2  ptys0  ptyve  ptyzc    tty39  ttybf  ttypd  ttyS3   ttyu9  ttyy7
fb0        ptya5  ptye3  ptys1  ptyvf  ptyzd    tty4   ttyc0  ttype  ttyS30  ttyua  ttyy8
fd         ptya6  ptye4  ptys2  ptyw0  ptyze    tty40  ttyc1  ttypf  ttyS31  ttyub  ttyy9
fd0        ptya7  ptye5  ptys3  ptyw1  ptyzf    tty41  ttyc2  ttyq0  ttyS32  ttyuc  ttyya
full       ptya8  ptye6  ptys4  ptyw2  ram0     tty42  ttyc3  ttyq1  ttyS33  ttyud  ttyyb
hda        ptya9  ptye7  ptys5  ptyw3  ram1     tty43  ttyc4  ttyq2  ttyS34  ttyue  ttyyc
hda1       ptyaa  ptye8  ptys6  ptyw4  ram10    tty44  ttyc5  ttyq3  ttyS35  ttyuf  ttyyd
hda2       ptyab  ptye9  ptys7  ptyw5  ram11    tty45  ttyc6  ttyq4  ttyS36  ttyv0  ttyye
hda5       ptyac  ptyea  ptys8  ptyw6  ram12    tty46  ttyc7  ttyq5  ttyS37  ttyv1  ttyyf
hdb        ptyad  ptyeb  ptys9  ptyw7  ram13    tty47  ttyc8  ttyq6  ttyS38  ttyv2  ttyz0
hpet       ptyae  ptyec  ptysa  ptyw8  ram14    tty48  ttyc9  ttyq7  ttyS39  ttyv3  ttyz1
initctl    ptyaf  ptyed  ptysb  ptyw9  ram15    tty49  ttyca  ttyq8  ttys4   ttyv4  ttyz2
input      ptyb0  ptyee  ptysc  ptywa  ram2     tty5   ttycb  ttyq9  ttyS4   ttyv5  ttyz3
kmem       ptyb1  ptyef  ptysd  ptywb  ram3     tty50  ttycc  ttyqa  ttyS40  ttyv6  ttyz4
kmsg       ptyb2  ptyp0  ptyse  ptywc  ram4     tty51  ttycd  ttyqb  ttyS41  ttyv7  ttyz5
log        ptyb3  ptyp1  ptysf  ptywd  ram5     tty52  ttyce  ttyqc  ttyS42  ttyv8  ttyz6
loop       ptyb4  ptyp2  ptyt0  ptywe  ram6     tty53  ttycf  ttyqd  ttyS43  ttyv9  ttyz7
lp0        ptyb5  ptyp3  ptyt1  ptywf  ram7     tty54  ttyd0  ttyqe  ttyS44  ttyva  ttyz8
lvm        ptyb6  ptyp4  ptyt2  ptyx0  ram8     tty55  ttyd1  ttyqf  ttyS45  ttyvb  ttyz9
MAKEDEV    ptyb7  ptyp5  ptyt3  ptyx1  ram9     tty56  ttyd2  ttyr0  ttyS46  ttyvc  ttyza
mapper     ptyb8  ptyp6  ptyt4  ptyx2  random   tty57  ttyd3  ttyr1  ttyS47  ttyvd  ttyzb
md0        ptyb9  ptyp7  ptyt5  ptyx3  rtc      tty58  ttyd4  ttyr2  ttys5   ttyve  ttyzc
md1        ptyba  ptyp8  ptyt6  ptyx4  shm      tty59  ttyd5  ttyr3  ttyS5   ttyvf  ttyzd
md10       ptybb  ptyp9  ptyt7  ptyx5  snd      tty6   ttyd6  ttyr4  ttys6   ttyw0  ttyze
md11       ptybc  ptypa  ptyt8  ptyx6  sndstat  tty60  ttyd7  ttyr5  ttyS6   ttyw1  ttyzf
md12       ptybd  ptypb  ptyt9  ptyx7  stderr   tty61  ttyd8  ttyr6  ttys7   ttyw2  urandom
md13       ptybe  ptypc  ptyta  ptyx8  stdin    tty62  ttyd9  ttyr7  ttyS7   ttyw3  vcs
md14       ptybf  ptypd  ptytb  ptyx9  stdout   tty63  ttyda  ttyr8  ttys8   ttyw4  vcs1
md15       ptyc0  ptype  ptytc  ptyxa  tty      tty7   ttydb  ttyr9  ttyS8   ttyw5  vcs2
md16       ptyc1  ptypf  ptytd  ptyxb  tty0     tty8   ttydc  ttyra  ttys9   ttyw6  vcs3
md17       ptyc2  ptyq0  ptyte  ptyxc  tty1     tty9   ttydd  ttyrb  ttyS9   ttyw7  vcs4
md18       ptyc3  ptyq1  ptytf  ptyxd  tty10    ttya0  ttyde  ttyrc  ttysa   ttyw8  vcs5
md19       ptyc4  ptyq2  ptyu0  ptyxe  tty11    ttya1  ttydf  ttyrd  ttysb   ttyw9  vcs6
md2        ptyc5  ptyq3  ptyu1  ptyxf  tty12    ttya2  ttye0  ttyre  ttysc   ttywa  vcs7
md20       ptyc6  ptyq4  ptyu2  ptyy0  tty13    ttya3  ttye1  ttyrf  ttysd   ttywb  vcs8
md21       ptyc7  ptyq5  ptyu3  ptyy1  tty14    ttya4  ttye2  ttys0  ttyse   ttywc  vcsa
md22       ptyc8  ptyq6  ptyu4  ptyy2  tty15    ttya5  ttye3  ttyS0  ttysf   ttywd  vcsa1
md23       ptyc9  ptyq7  ptyu5  ptyy3  tty16    ttya6  ttye4  ttys1  ttyt0   ttywe  vcsa2
md24       ptyca  ptyq8  ptyu6  ptyy4  tty17    ttya7  ttye5  ttyS1  ttyt1   ttywf  vcsa3
md3        ptycb  ptyq9  ptyu7  ptyy5  tty18    ttya8  ttye6  ttyS10 ttyt2   ttyx0  vcsa4
md4        ptycc  ptyqa  ptyu8  ptyy6  tty19    ttya9  ttye7  ttyS11 ttyt3   ttyx1  vcsa5
md5        ptycd  ptyqb  ptyu9  ptyy7  tty2     ttyaa  ttye8  ttyS12 ttyt4   ttyx2  vcsa6
md6        ptyce  ptyqc  ptyua  ptyy8  tty20    ttyab  ttye9  ttyS13 ttyt5   ttyx3  vcsa7
md7        ptycf  ptyqd  ptyub  ptyy9  tty21    ttyac  ttyea  ttyS14 ttyt6   ttyx4  vcsa8
md8        ptyd0  ptyqe  ptyuc  ptyya  tty22    ttyad  ttyeb  ttyS15 ttyt7   ttyx5  vmmon
md9        ptyd1  ptyqf  ptyud  ptyyb  tty23    ttyae  ttyec  ttyS16 ttyt8   ttyx6  vmnet0
mem        ptyd2  ptyr0  ptyue  ptyyc  tty24    ttyaf  ttyed  ttyS17 ttyt9   ttyx7  xconsole
mixer      ptyd3  ptyr1  ptyuf  ptyyd  tty25    ttyb0  ttyee  ttyS18 ttyta   ttyx8  zero
net        ptyd4  ptyr2  ptyv0  ptyye  tty26    ttyb1  ttyef  ttyS19 ttytb   ttyx9
null       ptyd5  ptyr3  ptyv1  ptyyf  tty27    ttyb2  ttyp0  ttys2  ttytc   ttyxa
nvidia0    ptyd6  ptyr4  ptyv2  ptyz0  tty28    ttyb3  ttyp1  ttyS2  ttytd   ttyxb
nvidiactl  ptyd7  ptyr5  ptyv3  ptyz1  tty29    ttyb4  ttyp2  ttyS20 ttyte   ttyxc
parport0   ptyd8  ptyr6  ptyv4  ptyz2  tty3     ttyb5  ttyp3  ttyS21 ttytf   ttyxd
[/HTML]

Is this something crucial?  I am still able to use my Ubuntu without errors.  When will I start to show errors if nothing is done?  How do I free up the /dev/hda1? ](*,) 


Thanks,
Zmartant

---

### Post by orb9220 on 2006-10-02
run a gksudo nautilus turn on show hidden files and check your /home/ and / and empty your .Trashcan people forget sometimes that there are more than one.

---

### Post by zmartant on 2006-10-02
orb9220,

Thank you for your tip!  I followed the culprit to VMware.  For some reason it ballooned XP.  I have delete everything that had to do with XP after deleting the client from VMware.  When I deleted XP via VMware, it remove the client from VMware, but did not delete XP from the clien directory.  I had to manually delete the files.  I will try and reinstall XP and see if it will baloon again.

My current df -h :
[HTML]
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.7G   32G   8% /
varrun                126M   92K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M   88K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-27-386/volatile
[/HTML]
This issue has been such a learning experience and will have to go into my Ubuntu wiki!  Thanks again orb9220 :KS !

-Zmartant

---

