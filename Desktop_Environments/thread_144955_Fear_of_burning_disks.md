---
title: "Fear of burning disks"
date: 2006-03-15
forum: Desktop Environments
---

### Post by linmick on 2006-03-15
Hello,

I have a questions and a fear perhaps an irrational one. Is it safe in linux to burn cd's  esp with gnomebaker? The reason I ask because in the past "2" (different manufacturers) of my cdrw  drives stopped working properly. 

1st drive: The door stopped ejecting without a pin. Without the proper close it kept telling me invalid  sensor  something sent  nocmd_error.  ( hope it was just a mechanical problem not firmware overwriten?)

2nd drive:  It no longer was able to write disks higher then 4x in any operating system or read high quality disks above 4x. Although the  media was supported and the good quality.   (Again  could it be  firmware overwriten?)

Is this all coincidence?

Did not do anything to the drive, burned none root etc.  So is it possible to damage the drive in any shape or form in linux just by trying to burn something?  Could a  buffer underrun in   linux kill the drive?  Could improper  closure  (while burning  no further write) of the  disks  destroy it in linux too?

Why  I base  "linux" is because it works different then windows. Wondering if the  precautions are different. Such as when it talks to the drive with commands. 

Aside from  doing something stupid  and physically  damaging the drive. Or, intentionally overwriting firmware how safe is linux to the drive? or better yet, not the kernel itself the applications  for it  esp "cdrecords" the one most common.  Could one destroy a  drive from improper  burn given the media is  good quality not scratched etc.  Thanks.

Again my fears  may / may not  be irrational but two drives went bad in short period of a year.

---

### Post by StefanoCole on 2006-03-16
Well, to me it sounds very strange the possibility to destroy a drive by improper burning. An improper burning could produce only a CD or DVD coaster. Also I don't think it is possible to damage (i.e. overwrite) the firmware accidentally. 
CD and DVD recorder manufacturers periodically provide firmware upgrades of their products in order to fix bugs or add compatibility to new media. So if your burner has problems you can try to update the firmware. Together with the new firmware the manufactures provide a software utility to perform the EEPROM burning. So, unless you use such utility you cannot overwrite the firmware. If you are going to upgrade the firmware be sure to not power off the PC while upgrading, since if this happens you will end with a damaged firmware.

Stefano

---

### Post by taurus on 2006-03-16
If you're afraid gnomebaker "bakes" your CD drive, then you may want to check out k3b then but I don't think gnomebaker or any burning program would cause a damage to your CD drive, not likely...

---

### Post by linmick on 2006-03-16
Thank You for the answers just got notified.  They seemed very thoughtful in trying to answer my question.  How about developers themselves what  do you think?

Same thought  not sure what to think about what happened to me? One would think that it would just make the "CDR" bad or a bad write on a cdrw.

> Well, to me it sounds very strange the possibility to destroy a drive by                                    > improper burning. An improper burning could produce only a CD or DVD                                     > coaster. Also I don't think it is possible to damage (i.e. overwrite) the                                     > firmware accidentally. 

The 1st drive was  beyond repair as seems the sense flag went  besides the door. The second  does not have one created for it.  I purchased "1" of the drives at newegg the other at tigerdirect. The second one has a  10% survival rate of exiting its state.

> CD and DVD recorder manufacturers periodically provide firmware upgrades                               > of their products in order to fix bugs or add compatibility to new media. So                              >  if your burner has problems you can try to update the firmware. Together                              >  with the new firmware the manufactures provide a software utility to                                     > perform the EEPROM burning. 

Again my thought... Developers????
> > So, unless you use such utility you cannot overwrite the firmware. If you                              > are going to upgrade the firmware be sure to not power off the PC while                                  > upgrading, since if this happens you will end with a damaged firmware.

Stefano

I recall one time  accidently having a mishap in the speed of  burning with gnomebaker or some sort with the 2nd drive. Do not remember that well at this point.  I am making full time linux switch but  burning  "will" have to be careful or something.

> If you're afraid gnomebaker "bakes" your CD drive, then you may want to                                 > check out k3b then but I don't think gnomebaker or any burning program                                 >  would cause a damage to your CD drive, not likely...

Taurus


-Mick

---

### Post by taurus on 2006-03-16
What brand names were those burners that pressumely gnomebaker destroyed!  I have Sony, NEC, Toshiba, & Lite-On and they are working fine...

---

### Post by MacV on 2006-03-16
The only thing that broke my cd burner was, ironically enough, one of those Walgreens photo cds. Popped it in, and the drive started making funny noises and that was the end of that. Burning disks however, I've never had an issue.

---

### Post by linmick on 2006-03-16
[QUOTE=taurus]What brand names were those burners that pressumely gnomebaker destroyed!  I have Sony, NEC, Toshiba, & Lite-On and they are working fine...[/QUOTE]
[QUOTE=MacV]The only thing that broke my cd burner was, ironically enough, one of those Walgreens photo cds. Popped it in, and the drive started making funny noises and that was the end of that. Burning disks however, I've never had an issue. [/quote]

The  1st drive was a CyberDrive C range   think  C60 or  C70. (threw it away beyond repair)
The 2nd drive   removed it from cardboard looking at its id marker. Forgot off the top of my head the name here is maybe the code. CR-485GTE and lists a  label with firmware ok.

**_First I do not want to fully blame gnomebaker yet._** I refuse to do so without any formal  knowledge. But remember had a speed issue thing but unsure it  is what broke it. However  I could swear by: "Popped it in, and the drive started making funny noises". If memory  coming back  now I remember i popped in a  Radio Shack CD "Ritadata"  and the 2nd drive powered  up and  it started to make crackling noise. The media was actually empty  but like MacV said nearly same.  Except, with me the 2nd drive  did not die it no longer reads "well" like  posted  before.  Could anyone  confirm that what  happened to MacV and me (lets forget the 1st drive just focus on 2nd). The  1st  drive  is suspicious too but still.  Hum...  if anyone else  comes out  and it will be a pattern  on this thread.  We will need to start looking for the cause. Because  sure  noone wants to have drives  dying  from just trying to burn under normal conditions.  Their was a  case were  some firmware and distro overwriten a  certain drive. Remember?  was that  a  user initiating the  overwrite or  it did it itself?

---

### Post by MacV on 2006-03-18
Great, so I'm not the only one then. After I removed the Walgreens disk, no disk could ever read again on the thing. The comp would see it, but my guess is that the laser either died, or the stupid cd borked the mechanism of the burner. Really pissed me off.:evil:

---

### Post by taurus on 2006-03-18
So it could be that crappy cheapo Walgreen CD that killed your CD burner!!!

---

### Post by linmick on 2006-03-18
[QUOTE=MacV]Great, so I'm not the only one then. After I removed the Walgreens disk, no disk could ever read again on the thing. The comp would see it, but my guess is that the laser either died, or the stupid cd borked the mechanism of the burner. Really pissed me off.:evil:[/QUOTE]

[QUOTE=taurus] 

 	So it could be that crappy cheapo Walgreen CD that killed your CD burner!!!  [/QUOTE]

Yup, maybe the media that is "rated" as good is to blame.

---

### Post by linmick on 2006-05-02
Hello all,

I am trying to flash my cdrw anyone  know how in linux? I tried using wine but it said the files were not found.The  flash program just was having hard time to see its own files. The  flasher for the driver is  for dos or windows. None  for linux. Any way to go with flashing?

Anyone  flashed anything under linux?  :neutral: (in thought but not sad)        8) 

Thanks

---

