---
title: "Grade 4 classroom using old laptops with Lubuntu"
date: 2018-11-05
forum: Education &amp; Science
---

### Post by valpritchard on 2018-11-05
Brand new to Lubuntu.  Looking for direction to a good thread/group regarding the use of Lubuntu, offline, in an elementary school classroom.

Making use of out of date laptops that are too old for Windows

Class of 27 grade four students - regular stream with many levels of differentiation

Offline...
1.  so I don't have to get permission by my school division technology crew to put these in the school.  If I ever need to  get new software or updates I would just use the hotspot from my phone.
2.  so I don't have to monitor my students watching junk youtube videos when i'm not looking
3.  so the computer doesn't get cluttered with junk
4.  so the computer starts faster

Software - all offline...(looking for recommendations)

keyboarding - something good.  I would prefer something that I could set up six or so user accounts, preferably with a password or pin, so students can progress at their own level and not mess with someone else's account.  With five computers I would assign five kids to take turns on one of the computers, using the same computer all the time.

math - something that reinforces basic math facts - addition, subtraction, multiplication, division

Sight words - mostly for EAL students and students with learning disabilities who haven't yet mastered these.

Word Processor - similar to Word that students can save to hard drive or to removable usb drive
Spreadsheet - same as above
Presentation - same as above
Probably use Libreoffice - but maybe something better?

wondering what else you are using, advice, recommendations, etc.
Thanks!
Val

---

### Post by TheFu on 2018-11-05
If they are never on a network, then I wouldn't worry about patching until some dependency forced it.  Just make certain you are 100% patched before you clone the install across each of the systems.

Thought there was an educational version of Ubuntu?  Let me google that ... [https://www.edubuntu.org/](https://www.edubuntu.org/)
[https://liliputing.com/2016/03/edubuntu-linux-will-skip-ubuntu-16-04-lts-release.html](https://liliputing.com/2016/03/edubuntu-linux-will-skip-ubuntu-16-04-lts-release.html) - seems that project is dead. Too bad.  But maybe the list of packages used in that release would give you some ideas?   In no way would I use the 14.04 release. Support for it ends in a few months, so any work you do would need to be redone anyways.

I would setup a script to create user accounts for 30 students and assign 1 to each kid.  useradd or adduser is the command. It would take under a second to run.  I would completely disable all networking - hard locking any wifi capabilities - to prevent students from even attempting to connect to school wifi.

Old computers will have issues. I hope things go easy, but they probably will not. Disks will fail, screens will fail and some keys on the keyboards might not work.  Each computer will have different issues and some won't have sufficient RAM to run any ubuntu well.

If you are totally new to Unix-like systems, doing this will be a steep hill to climb, I'm afraid.

---

### Post by Frogs Hair on 2018-11-05
The hardware specs for the older computers is huge question. Verifying that Lubuntu could run on them would be a first step.  

[https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/](https://lubuntu.net/lubuntu-18-04-bionic-beaver-released/)

---

### Post by valpritchard on 2018-11-09
Thank you.  Great info.

---

### Post by valpritchard on 2018-11-09
Excellent link.  It helps me narrow down more closely if this will work.
Thank you.

---

### Post by sudodus on 2018-11-09
> **valpritchard said:**
> Brand new to Lubuntu.  Looking for direction to a good thread/group regarding the use of Lubuntu, offline, in an elementary school classroom.


New to Lubuntu, but maybe you have some experience of some other linux distro?
> 
Software - all offline...(looking for recommendations)

It is rather easy to find suitable application programs that work online via the internet. Let us hope that you find useful things, that work locally in linux.
> 
keyboarding - something good.  I would prefer something that I could set up six or so user accounts, preferably with a password or pin, so students can progress at their own level and not mess with someone else's account.  With five computers I would assign five kids to take turns on one of the computers, using the same computer all the time.

math - something that reinforces basic math facts - addition, subtraction, multiplication, division

Do you want game-like programs?

I found several internet links via the search string **linux math children**.

Would a program like **octave** do? Please notice that **LibreOffice Calc** can be used for such tasks too. Download, expand and check the attached gzip-compressed file,

```

$ zcat multiplikationstabellen.ods.gz > multiplikationstabellen.ods
$ md5sum multiplikationstabellen.ods*
e5b20d89f103bc0db2b8e81dd32a5c4c  multiplikationstabellen.ods
68d55d392557703f8911b8b6d75b219e  multiplikationstabellen.ods.gz

```

And there are several small calculator programs, Lubuntu 18.04 LTS comes with **galculator**.
> 
Sight words - mostly for EAL students and students with learning disabilities who haven't yet mastered these.

I find nice web applications, but nothing local for linux. I played around a little and made the shellscript **speak-words**, which needs the programs **zenity** and **espeak**.

```

#!/bin/bash

list=
ppr_an="a and away big blue can come down find for funny go help here I in is it jump little look make me my not"
ppr_oy="one play red run said see the three to two up we where yellow you"
pr_ao="all am are at ate be black brown but came did do eat four get good have he into like must new no now on our out"
pr_py="please pretty ran ride saw say she so soon that there they this too under want was well went what white who will with yes"
gr1="after again an any as ask by could every fly from give giving had has her him his how just know let live may of old once open over put round some stop take thank them then think walk were when"
gr2="always around because been before best both buy call cold does don't fast first five found gave goes green its made many off or pull read right sing sit sleep tell their these those upon us use very wash which why wish work would write your"
gr3="about better bring carry clean cut done draw drink eight fall far full got grow hold hot hurt if keep kind laugh light long much myself never nine only own pick seven shall show six small start ten today together try warm"
nn="apple baby back ball bear bed bell bird birthday boat box boy bread brother cake car cat chair chicken children Christmas coat corn cow day dog doll door duck egg eye farm farmer father feet fire fish floor flower game garden girl good-bye grass ground hand head hill home horse house kitty leg letter man men milk money morning mother name nest night paper party picture pig rabbit rain ring robin Santa_Claus school seed sheep shoe sister snow song squirrel stick street sun table thing time top toy tree watch water way wind window wood"

text="Double-click to select word list"
espeak "$text" &
list=$(zenity --list --text "$text" --title="Word lists" \
 --column "list-name" --column="list" --print-column=2 \
 --height=400 \
 --width=300 \
 ppr_an "$ppr_an" \
 ppr_oy "$ppr_oy" \
 pr_ao  "$pr_ao" \
 pr_py  "$pr_py" \
 gr1 "$gr1" \
 gr2 "$gr2" \
 gr3 "$gr3" \
 nn  "$nn" \
 2>/dev/null)
if [ "$list" == "" ]
then
 exit
fi

if [ "$list" == "$gr1" ] || \
   [ "$list" == "$gr2" ] || \
   [ "$list" == "$gr3" ] || \
   [ "$list" == "$nn" ]
then
 espeak "Scroll down, to find the words, near the bottom of the list"
 sleep 1
fi
text="Double-click on a word and listen to it"
espeak "$text" &
cont=true
while $cont
do
 word=""
 word=$(zenity --list \
  --text "$text" \
  --title="Selected word list" \
  --hide-header \
  --column "word" \
  --height=720 \
  --width=300 \
  $list \
  2>/dev/null)
 if [ "$word" != "" ]
 then
  espeak "$word"
 else
  cont=false
 fi
done

```
> 
Word Processor - similar to Word that students can save to hard drive or to removable usb drive
Spreadsheet - same as above
Presentation - same as above
Probably use Libreoffice - but maybe something better?

I agree about LibreOffice.
> 
wondering what else you are using, advice, recommendations, etc.
Thanks!
Val

---

