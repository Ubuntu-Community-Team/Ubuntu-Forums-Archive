---
title: "How to convert *.bgl (babylon) to stardict *.ifo"
date: 2009-01-19
forum: General Help
---

### Post by Thura on 2009-01-19
I have been trying to convert a bgl file from babylon to use with my stardict for three weeks ...
Most of the how-to's on the Internet doesn't work anymore with the new encrypted *.bgl files !
I have tried stardict-editor, dictconv, and several others ...
None of them worked !

But, after three weeks of searching I figured out a way to convert ...
I saw some unanswered threads about this, and post it here as somebody might wanna know this ...

This is a step-by-step how-to ...

(1) First, download the UnpackBGL.exe [here]("http://uploads.bizhat.com/file/377004"). ( Originally, from a reverse-engineering forum )
(2) Then, run it with wine or in Windows
(3) Open your bgl file and blah blah ...
(4) Then, you will have *.bgl.txt in the same directory ...
(5) You cannnot convert it directly to stardict with stardict-editor
(6) So, you have to convert it to tab dictionary file then to stardict's ifo format ...

What is tab file 
----------------
Here is a example dict.tab file:
============
a	1\n2\n3
b	4\\5\n6
c	789
============
It means: write the search word first, then a Tab character, and the definition. If the definition contains new line, just write \n, if contains \ character, just write \\. ( quoted from official site )

How to convert
--------------
Well, by-hand is not possible if your dictionary is large ...
You can use sed, python, perl or anyth to convert your txt file to tab format ....

Here is an example of python script I used to convert my file ... 
You cannot use this for your case, as different dictionaries can give different output ...
I am not an experienced programmer, still learning python ...
For regular expressions, I first tested with kiki, a must-have software if you are planning to learn regular expression ...

```
#!  /usr/bin/env python
# -*- coding: utf-8 -*-

import re

inputFile  = " "	#input file ( *.bgl.txt converted with file
outputFile = " "	#output file

#Read File
try:
    inFile = open(inputFile,"r")
except IOError:
    print "Cannot open the input file!"
    sys.exit(1)
content = inFile.read()
inFile.close()

#==========
#Conversion
#==========
removeCSS  = re.compile("[.#].+\s*{[^}]*?}")                        #pattern to remove CSS
removeHTML = re.compile("<[^>]*>",re.M)                             #pattern to remove HTML
removeEmptyLines = re.compile("\s+\n\n", re.M)                      #pattern to remove Empty Lines
replaceTabs      = re.compile("^\t",re.M)                           #pattern to replace lines starting with tabs
removeBC         = re.compile("\s&#9679;\s+")                             #pattern to remove &#9679;
newlinestr = re.escape("\\n")

content = removeCSS.sub("",content)             #remove CSS
content = removeHTML.sub("",content)            #remove HTML
content = replaceTabs.sub(newlinestr,content)   #replace lines starting with Tabs
content = removeEmptyLines.sub("\t",content)    #remove Empty Lines
content = content.replace("\n\\n","")           #replace new lines before "\n" string
content = removeBC.sub(newlinestr,content)      #replace &#9679; with "\n"
inFile.close()

#Write File
try:
    outFile = open(outputFile,"w")
except IOError:
    print "Cannot open the output file"
outFile.write(content)
outFile.close()

print "Fin"
```

(7) If all goes well, now you have a tab dictionary file, install "stardict-tools",then run -> stardict-editor -> load your file ->  build 

(8) Now, you will have three files in that directory ... *.dict.dz *.ifo *.idx

(9) Make a new folder in /usr/share/stardict/dict/, then put those three files in that folder ....

Now, you are finished .... 
But, believe me it wasn't that easy for me , it took me three weeks to figure that out .. ;(

---

### Post by Dwaalspoor98 on 2009-03-02
Thanks a lot for posting! Now I can also convert the newer dicts :)

---

### Post by binbash on 2009-03-02
This is the best post i have seen this month : ) It works great

---

### Post by agnes on 2009-04-08
It doesn't work for me.

I've downloaded UnpackBGL but when I open a fresh downloaded Dutch-English BGL dictionary in it, the program says: "Readpoint not found". If I adjust some options (with the checkboxes), it just says: "I/O error 32".

Or should I download the offline-dictionary (.exe), explore/open it and extract the .BGL file from there?

---

### Post by Thura on 2009-04-08
It actually shows a lot of errors when I convert my file.
But, the important thing is do you have *.bgl.txt in the same folder ? If you have, don't care about the errors, just proceed to the next step.

>should I download the offline-dictionary (.exe), explore/open it and extract the >.BGL file from there?
I think it will give the same result, as it is going to be same file.

---

### Post by agnes on 2009-04-08
I indeed got those files. However, they are of 0 bytes, there is no data within them. Just empty. :-?

(I downloaded program to USB stick, then rebooted to Windows Vista, copy program to some dir., run program.)

Getting a file of zero bytes, was also the case when I tried to convert .BGL files with dictconv, by the way. (Ok, I know this should not be able to work anyway, since Babylon has 'updated' their .BGL files, but maybe you got a file with actually *some* data in it... here, only the .ifo file contained data.

[***Update**: No need to convert, one can still download the stardict versions of babylon dictionaries at [http://reciteword.sourceforge.net/stardict/babylon.php]("http://reciteword.sourceforge.net/stardict/babylon.php") - I could just extract it (get .idx, .ifo, .syn and .dict.dz files) and then place that extracted directory in StarDict's dic directory.* ]

---

### Post by jeroenvrp on 2009-04-22
It's even easier now using StarDict 3.0.1.

1. Install Babylon under Wine and enable during setup the dictionaries you need. Please use a terminal.
2. cd  ~/.wine/drive_c/Program\ Files/Babylon/Babylon-Pro/Data/BGLs (ATTENTION: Program Files can be translated to your own language)
3. Copy the .BGL-file you need to ~/.stardict (don't use the smaller ...sub.bgl files, but the ones without "sub" and with a larger file size)
4. cd ~/.startdict
4. Launch stardict-editor (from the commandline - it makes sure the output is in .stardict)
5. Press "Browse" and choose the .BGL-file you just copied.
6. Select "BGL file" on the bottom left of the window.
7. Press "Build" next to it.
8. When it is ready go back to "Browse" and choose the file with the same base name, but with a .babylon extension.
9. Select "Babylon file" on the bottom left of the window.
10. Press "Build" next to it.
11. Copy all files just created (except the .babylon-file and the .BGL-file) from  ~/.stardict to ~/.stardict/dict (probably 4 files)
12. Restart StarDict.
13. Don't forget to uninstall Babylon from wine. You won't need it anymore. ;-)

I just tell this, because the files listed on [http://reciteword.sourceforge.net/stardict/babylon.php](http://reciteword.sourceforge.net/stardict/babylon.php) are not exactly the same as directly from Babylon. The Dutch-English dictionary for example is almost twice as large.

---

### Post by agnes on 2009-04-24
Sorry, but what do you mean with

4. Launch start=editor 

?

Don't have a program called like that.

---

### Post by Thura on 2009-04-24
Install stadict-tools ... then run stardict-editor ...
```
sudo apt-get install stardict-tools
stardict-editor
```

---

### Post by agnes on 2009-04-24
Ok thanks, didn't know such a tool existed anyway.

But the dictionaries (those from sourceforge and those converted using jeroenvrp's method) are the same.
 That is, they have the same wordcount (according to Stardict, 3.0.1) and also give me the same results. (I've tested with Dutch-->English and English-->Dutch.) 
Probably those from sourceforge are just made from those .BGL's.
(Not from the .sub.BGL's.)

(*Edit*: just found out that UnpackBGL.exe does work well on XP, probably just a Vista issue. But this also gives me dictionaries of the same length as those on sourceforge.)
(*Edit again*: to be complete: sorry, it's probably nót a Vista issue, I just used the .sub.BGL's for UnpackBGL.exe the first time :roll:)


 Or did anyone get different results? (Between the dictionaries converted and those from sourceforge.)

---

### Post by arielmazin on 2009-09-17
Hi!
 
I have windows:( so i be happy that you can help me 
convert *.bgl (babylon) to stardict *.ifo if you can
 
sicerely,
Ariel

---

### Post by janerds on 2010-03-15
Does anyone know how to convert Babylon bdc file to stardict format?

I have lots of bdcs, but did not find any way to convert these files.

Thanks

---

### Post by go_beep_yourself on 2010-04-21
Where exactly can I get the babylon dictionaries?

---

