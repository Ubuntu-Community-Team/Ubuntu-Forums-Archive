---
title: "How to type Greek in Latex and the greektex package"
date: 2008-05-28
forum: Education &amp; Science
---

### Post by tekkenlord on 2008-05-28
This is a tutorial on how to install the greektex package [(http://www.research.dryllerakis.gr/greektex.html)]("http://www.research.dryllerakis.gr/greektex.html") on Ubuntu. It should work on other LinuX distributions as well. There are other alternatives for typing in Greek in LateX, see for example [http://ubuntuforums.org/showthread.php?t=697569]("http://ubuntuforums.org/showthread.php?t=697569"). However, most of the other packages require to insert a command before typing in Greek or English (based on Babel).

I presume you are using texlive and not tetex. Besides, texlive is more recent and I think that the development on tetex has stopped. 

The greektex package can be found in the ubuntu repositories. However, it does not work "out of the box". You will need to copy some files to the appropriate directories in your TeX path. 

There are instructions for these  (found on the greektex link posted earlier) but IMHO they are out of date. That's why I decided to write this simple guide based on the original instructions. Ok, let's start!


The STEPS:

1) Install unzip and gzip, if you do not have it already, with:

**sudo apt-get install unzip gzip;**



2) Install the greektex package:

**sudo apt-get install texlive-lang-greek;**
 
 
 
3) Issue in a terminal the following commands:

**sudo unzip /usr/share/doc/texlive-lang-greek/latex/greektex/ywcl.zip -d /usr/share/texmf-texlive/fonts/source/public/ywcl;**

**sudo gzip -d /usr/share/doc/texlive-lang-greek/latex/greektex/gehyphw.gr.gz;**

**sudo mv /usr/share/doc/texlive-lang-greek/latex/greektex/gehyphw.gr /usr/share/texmf-texlive/tex/generic/hyphen/;**



4) Open with your favourite editor the file **/etc/texmf/language.d/09texlive-base.cnf** (you will need root access, use sudo). **NOTE:** If you are using recent distros (10.04) you will have to edit **/usr/share/texmf-texlive/tex/generic/config/language.us** instead.

Find the line that reads:

english		hyphen.tex  % do not change!

and change it to

english		hyphen.tex  [COLOR="Blue"]gehyphw.gr[/COLOR]   % do not change!




5) In a terminal type:

**sudo update-language;**

**sudo texhash;**

**sudo fmtutil-sys --all; **


The very last step is essential for the hyphenation to work correctly. Full credit and many thanks go to user eumataxas for spotting this, correcting it and making this guide complete.

That's it. Make sure that when you type Greek in your LateX editor (I use Kile) you have the encoding [COLOR="Blue"]**"Greek iso-8859-7"**[/COLOR], otherwise you will get weird fonts in the DVI, PDF etc. I attach a TeX document using the greektex package. Rename it to "greek.tex" and use it to check whether greektex works properly.

Good luck!

Keywords: greektex, latex, linux, ubuntu, greek

---

### Post by eumetaxas on 2008-06-29
hi and thanx for that post.
i've been using greektex for about a year with no prlblems. suddenly (probably after upgrading  to ubuntu 8.04) hyphenation does not work. i've tried installing and re-installing, a couple of tutorials but hyphenation still does not work!
any help? xgreek hyphenation stopped too. babel hyphenation got back after a lot of experiments!
thanx in  advance!
&#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#969;!

---

### Post by tekkenlord on 2008-06-29
Hi and you are welcome! I do not quite understand. How exactly are you using the hyphenation? Do you input the dashes manually (like this?    *syl_1*[COLOR="RoyalBlue"]**\-**[/COLOR]*syl_2*   ) or do you have a file containing the hyphenation of the words?  Does the hyphenation work when used with English or is it just the Greek?

---

### Post by eumetaxas on 2008-06-30
Thanx for your quick answer!

inside greektex package there's a file that i think is with hyphenation rules.
"gehyph.gr" and documentation coming with greektex (and your instructions) say to put that file in \usr\share\texmf\tex-texlive\generic\hyphen and also says to edit the language.dat file. All of this used to work perfectly and automatically. they still work i windows box at work. Suddenly hyphenation sropped working (as i've said probably after upgrade - i do not use texlive everyday). i reinstalled texlive-lang-greek, did everything again as the first time but still does not work. 
i am at work now but as i recall english is ok.
How do you use hyphenation with greektex?

Thanx again!

---

### Post by tekkenlord on 2008-06-30
To be honest I do not use greektex that much. I just installed it because I wanted to recompile a greek document I had written when I was using Windows. In that document, I use hyphenation with the slash and the dash, like this \-   and the word breaks up successfully. 

I am sorry if you have already tried this but can you check that the file /etc/texmf/language.d/09texlive-base.cnf contains exactly what I have written in the tutorial? Refer to step (4) of the tutorial. 

Can you also post a TeX document that you are having problems with? I can try it on my computer and check if I have the same problem. I am sorry for not being a big help so far...

Regards,
Giorgos

---

### Post by eumetaxas on 2008-06-30
&#964;&#959; &#945;&#961;&#967;&#949;&#943;&#959; 09texlive-base.cnf &#960;&#949;&#961;&#953;&#941;&#967;&#949;&#953; &#945;&#954;&#961;&#953;&#946;&#974;&#962; &#972;&#964;&#953; &#941;&#967;&#949;&#953;&#962; &#947;&#961;&#940;&#968;&#949;&#953; &#960;&#953;&#959; &#960;&#940;&#957;&#969; &#947;&#953;&#945;&#964;&#943; &#964;&#959; &#941;&#967;&#969; &#949;&#955;&#941;&#947;&#958;&#949;&#953; &#949;&#960;&#945;&#957;&#949;&#953;&#955;&#951;&#956;&#956;&#941;&#957;&#945;. &#924;&#941;&#961;&#959;&#962; &#964;&#959;&#965; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965; &#949;&#943;&#957;&#945;&#953; &#945;&#965;&#964;&#972; &#960;&#959;&#965; &#963;&#959;&#965; &#963;&#964;&#941;&#955;&#955;&#969; &#945;&#955;&#955;&#940; &#941;&#967;&#969; &#948;&#959;&#954;&#953;&#956;&#940;&#963;&#949;&#953; &#954;&#945;&#953; &#948;&#953;&#940;&#966;&#959;&#961;&#959;&#965;&#962; &#964;&#965;&#967;&#945;&#953;&#959;&#965;&#962; &#963;&#965;&#957;&#948;&#953;&#945;&#963;&#956;&#959;&#973;&#962; &#955;&#941;&#958;&#949;&#969;&#957; &#947;&#953;&#945; &#957;&#945; &#948;&#969; &#945;&#957; &#964;&#953;&#962; "&#963;&#960;&#940;&#950;&#949;&#953;". &#913;&#965;&#964;&#972; &#960;&#961;&#941;&#960;&#949;&#953; &#957;&#945; &#957;&#945;&#953; &#947;&#949;&#957;&#953;&#954;&#972;&#964;&#949;&#961;&#959; &#960;&#961;&#972;&#946;&#955;&#951;&#956;&#945; &#964;&#959;&#965; greektex &#947;&#953;&#945; GNU/LINUX &#947;&#953;&#945;&#964;&#943; &#964;&#959; &#941;&#967;&#969; &#946;&#961;&#949;&#953; &#954;&#945;&#953; &#963;&#949; &#940;&#955;&#955;&#945; Posts &#963;&#964;&#959; Google &#967;&#969;&#961;&#943;&#962; &#972;&#956;&#969;&#962; &#955;&#973;&#963;&#951;. &#931;&#964;&#945; Windows &#972;&#955;&#945; &#954;&#945;&#955;&#940;. &#924;&#940;&#955;&#955;&#959;&#957; &#972;&#960;&#969;&#962; "&#967;&#940;&#955;&#945;&#963;&#949;" &#945;&#965;&#964;&#972;&#956;&#945;&#964;&#945; &#960;&#961;&#941;&#960;&#949;&#953; &#954;&#945;&#953; &#957;&#945; &#966;&#964;&#953;&#940;&#967;&#957;&#949;&#964;&#945;&#953;!
&#917;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; &#960;&#959;&#955;&#973;!
&#917;&#965;&#947;&#941;&#957;&#953;&#959;&#962;

---

### Post by tekkenlord on 2008-06-30
Hi again, keep writing English, we might get reported. So, I tested the file you sent me and you are very right. It does not work on me either unless I manually break it (check the file I attach). Sorry but I do not know what is wrong, I will try and play with it a bit more. If I find anything, I will let you know. Kali sinexeia file!

---

### Post by eumetaxas on 2008-06-30
thanx!
did not know that we might get reported! saw some spanish guys writing and thouhgt it was ok.sorry for that.
thanx a lot my friend. i'll wait for your, or anybody's alse, suggestions!
thanx again!

---

### Post by eumetaxas on 2008-07-01
probably the only extra necessary step is the last one!

1.Complete uninstall texlive
2.minimal new install ~200mb
3.Copied hyphenation (gehyphw.gr) file as said in step 3 of tutorial
4.edited language.dat file in /var/lib/texmf/tex/generic/config/language.dat and added gehyphw.gr as said in tutorial
5. taxhash  AND 
6.  sudo fmtutil-sys --all

and works like a charm!!!

thank you and especially tekkenlord!

---

### Post by tekkenlord on 2008-07-02
You are the best. I tried only the last step without uninstalling anything and it worked perfectly! I will add your last step in the tutorial and give you full credit. Thank you!

---

### Post by xaris106 on 2008-07-08
Does this work with Lyx? I did all the previous and wrote some stuff in lyx in greek, then alt-shifted to english, typed some english words and saved
When I watch the dvi I get the english words with greek characters still...
Please help. I want to write my thesis in Latex and I have loads of troubles.
See [http://ohioloco.ubuntuforums.org/showthread.php?t=853335]("http://ohioloco.ubuntuforums.org/showthread.php?t=853335") for what I am trying to do and if you can help me. Thanks a lot in advance.

---

### Post by xaris106 on 2008-07-08
hmm ok i managed to make it half work...
basically as i understand it with those instructions i can write greek text inside an english document. It works when I set the language of Lyx to english..
But I would like the opposite, meaning i want to add english words in greek document beacause i want the "table of contents" "chapter 1" etc to be displayed in greek. and also i want a wotking greek spellchecking..
How i can do this?

---

### Post by tekkenlord on 2008-07-15
Hi Xari, sorry for the late reply, I just saw your posts. I have never used Lyx before so I am not sure if i can help you. I understood what you are trying to do, I will check it and if I find anything, I will post back.

---

### Post by eumetaxas on 2008-07-17
Hi from me too, i was away.
I have never used lyx also so unable to help

why don't you try a normal editor such as **texmaker**?
i am using it for a year now (as long as i use latex), it's multiplattform, easy to use and helped me as a latex newbie

---

### Post by Nikos.Alexandris on 2008-09-20
Hi to all!

A couple of weeks ago I managed to get "greek" words in an english text using the tutorial posted in page 1 using LyX. Now, after upgrading LyX (compiled from source code) can't seem to get it work properly. If I use encoding "Unicode (XeTeX) (utf8)" I get greek words but I lose other characters (for example the "&#8211;" appears as "â&#8364;&#8220;"). Any help would be highly appreciated.

Thank you, Nikos

---

### Post by Nikos.Alexandris on 2008-09-20
I've just compiled the latest LyX source code and everything works again. I think that inbetween I installed some lyx.xxx.deb package from getdeb.net [1]

Thanks for this tutorial :-)

[1] [http://www.getdeb.net/search.php?keywords=lyx](http://www.getdeb.net/search.php?keywords=lyx)

---

### Post by flwros on 2008-10-30
Hello to everybody. i encountered a problem with Lyx writing greek letters, more specifically with greek sigma. In more detail, when i write it outputs &#963; -> sv, &#962; -> c. Has anybody else found this problem? I use Lyx 1.5.6 and texlive. I have already installed greektex!

Thanks in Advance

Basil

---

### Post by Stefan_K on 2008-10-30
Hi Basil,

could you post a small LyX file showing the problem as an attachment here? In that case we could test it to find the problem.

Stefan

---

### Post by flwros on 2008-10-30
Stefan, 

I place here a small example of code.
I use iso-8859-7 encoding for Greek 

Basil

---

### Post by Stefan_K on 2008-10-30
I've copied this small code snipped into a LyX document, both symbols were printed, no sv or c instead.
This way I cannot reproduce your problem. But with a complete LyX file, even if it would be short, I would have a chance to reproduce that error.

Stefan

---

### Post by flwros on 2008-10-31
I made a test, and i changed to babel. Everything seems to appear ok!

I think the problem should be with greektex!

---

### Post by flwros on 2008-11-01
I tried Winedt and greektex and everything seems to be fine. But, when i come to Lyx (1.5.6) and greektex the same problem, with the greek sigma and final greek simga, appears again. 


Is it a bug of Lyx?

---

### Post by Nikos.Alexandris on 2008-11-01
> **flwros said:**
> I tried Winedt and greektex and everything seems to be fine. But, when i come to Lyx (1.5.6) and greektex the same problem, with the greek sigma and final greek simga, appears again. 


Is it a bug of Lyx?

Hi!

Not sure... ! But why don't you try LyX 1.6.rc3? You can get a .deb package from [http://www.getdeb.net/search.php?keywords=lyx](http://www.getdeb.net/search.php?keywords=lyx) (attention: the link points to the 64-bit package but there is also a 32-bit version).

Regards

---

### Post by flwros on 2008-11-02
After many tests i figured out that this problem results if i place in the Latex preamble of the Lyx Document the following command:

\usepackage{greektex}


I have already placed this  at the Tools->Preferences->Language Options.

I have another question to pose: how "table of contents, chapter etc." appear in Greek"&#928;&#949;&#961;&#953;&#949;&#967;&#972;&#956;&#949;&#957;&#945;, &#922;&#949;&#966;&#940;&#955;&#945;&#953;&#959; &#954;&#964;&#955;."???

---

### Post by simosx on 2008-11-21
The popular way to type Unicode documents in Greek is to use xetex/xelatex.

For more information, see
[http://ubuntu.opengr.net/viewtopic.php?f=9&t=930](http://ubuntu.opengr.net/viewtopic.php?f=9&t=930)

When you type latin characters and the generated document shows Greek characters, then this issue relates to problematic encodings.
It is important to use a method that allows to type in Unicode.

---

### Post by flwros on 2008-11-24
Thanks everyone for their kind replies,

Finally, i managed to solve the problem "write greek in Lyx using greektex package". The solution is the encoding must be latin!!! and not iso-8859-7!!!

---

### Post by milia on 2009-12-17
Thank you Tekkenlord,eumetaxas !

Finaly an easy method of writing greek in tex(+Kile) ! :D

Great job.:KS

---

### Post by SexyFrisby on 2010-05-11
Thanks for the compact instructions!
I have followed them before, when I was running Ubuntu 8.04, and they worked fine.  However, after my upgrade to 10.04, there is a hickup.  In step 4), file** /etc/texmf/language.d/09texlive-base.cnf** doesn't exist, so I was not able to get correct hyphenation for Greek.

Looking around I located some files **language.dat** with the text
english        hyphen.tex  % do not change!
I changed it to
english        hyphen.tex  [COLOR=Blue]gehyphw.gr[/COLOR]   % do not  change!
... pretended that nothing happened and went on.  Well, Greek hyphenation still doesn't work :(

Any ideas are welcome.  Otherwise I'll keep getting overfull boxes!!  Can't let that happen, right?

---

### Post by SexyFrisby on 2010-05-12
I don't know if it's helpful, but I thought I might give more information...
The **language.dat** file that I am changing is **/var/lib/texmf/tex/generic/config/language.dat**.  There are links to it from other locations, which confused me in the beginning into thinking there are multiple files.  "locate language.dat" doesn't seem to give any relevant results for other independent files.

If after adding gehyphw.gr to the aforementioned line I issue
**sudo update-language;**
the addition disappears and the line becomes again
english        hyphen.tex  % do not change!

If I skip the
[B]sudo update-language;
[/B]and issue directly:

**sudo texhash;**
(ends with no problem)
**sudo fmtutil-sys --all; **
gives me the following warnings/error


###############################################################################
fmtutil: Warning! Some warnings have been issued.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `warning' messages:
`xetex -ini  -jobname=xelatex -progname=xelatex -etex xelatex.ini' possibly failed.

###############################################################################
fmtutil: Error! Not all formats have been built successfully.
Visit the log files in directory
  /var/lib/texmf/web2c
for details.
###############################################################################

This is a summary of all `failed' messages:
`luatex -ini  -jobname=dvilualatex -progname=dvilualatex dvilualatex.ini' failed
`luatex -ini  -jobname=lualatex -progname=lualatex lualatex.ini' failed

I have no idea what luatex does!
Thanks...

---

### Post by SexyFrisby on 2010-05-13
News from the same front:
Checking the log files I found out that I'm getting these errors from gehyphw.gr because luatex can't understand the gehyphw.gr encoding (iso-8859-15).  From its log files:

(/usr/share/texmf-texlive/tex/generic/hyphen/gehyphw.gr
! String contains an invalid utf-8 sequence.
l.71 \lccode`
             ?=1
A funny symbol that I can't read has just been (re)read.
Just continue, I'll change it to 0xFFFD.

I resaved gehyphw.gr with utf-8 encoding, luatex goes past it, but then pdftex can't process gehyphw.gr!  From its log files:

(/usr/share/texmf-texlive/tex/generic/hyphen/gehyphw.gr
! Missing number, treated as zero.
<to be read again> 
                   ?
l.71 \lccode`á
               =1
A number should have been here; I inserted `0'.

What gives?  Any ideas for the encoding I should use for saving gehyphw.gr or other solutions?

---

### Post by tekkenlord on 2010-06-01
Hello,

Sorry for this late reply. I recently installed 10.04 myself but have not tested the instructions yet. I am doing so as I write this msg.

I noticed that I do not have the 09texlive-base.cnf in /etc/texmf/language.d but I do have it in /etc/texmf/hyphen.d (only there, nowhere else).

I will try editing that file and post back...

---

### Post by tekkenlord on 2010-06-01
Hmm, ok, apparently editing the /etc/texmf/hyphen.d/09texlive-base.cnf results in errors when running "sudo update-language". 

Nevertheless, I skipped that step and hyphenation seems to work correctly (at least for my tex documents).

Do you think you can send me one of the files that creates problem for you? 

Regards,
Giorgos

---

### Post by spinoza666 on 2010-06-01
> **eumetaxas said:**
> Thanx for your quick answer!

inside greektex package there's a file that i think is with hyphenation rules.
"gehyph.gr" and documentation coming with greektex (and your instructions) say to put that file in \usr\share\texmf\tex-texlive\generic\hyphen and also says to edit the language.dat file. All of this used to work perfectly and automatically. they still work i windows box at work. Suddenly hyphenation sropped working (as i've said probably after upgrade - i do not use texlive everyday). i reinstalled texlive-lang-greek, did everything again as the first time but still does not work. 
i am at work now but as i recall english is ok.
How do you use hyphenation with greektex?

Thanx again!

Hmmm,

I have no experience with greek in LaTex, but out of interest I downloaded your file and tried to open it in Kile. First it gave me an error message saying it was not in UTF8 encoding, and produced some scrambled text. So I sat the encoding autodetection to universal in the editor settings, and voila it opened the file (test.txt) and displaying perfect greek letters as far as I can tell.

So just an idea, have you tried setting the correct encoding in the settings of your editor. This may have changed since your upgrade.

EDIT: Sorry, I had on non-linear dispaly mode for the first time, and completely missed all the foregoing posts. My apologies, and disregard the above:)

---

### Post by tekkenlord on 2010-06-01
Ok, I found out what you need to do... Open the following file:

/usr/share/texmf-texlive/tex/generic/config/language.us
 
and you should see the line that reads 

english hyphen.tex % do not change!

and change it to

english hyphen.tex gehyphw.gr % do not change!

Follow step 5) of the guide and you should be fine.

Regards

---

### Post by ncs_one on 2010-11-09
I followed the 5 steps and everything works, except hyphenation in English. Hyphenation in greek works perfectly. Does anybody else have the same problem?

---

### Post by tekkenlord on 2010-11-09
Sorry, but no. Both greek and english work fine for me.

---

