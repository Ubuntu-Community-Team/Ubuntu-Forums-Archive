---
title: "How can I do an inverse search between  okular and kile?"
date: 2009-03-06
forum: General Help
---

### Post by ali780 on 2009-03-06
How can I do an inverse search between  okular and kile?
Or alternatively how can I change my dvi viewer in kile from okular to Kdvi viewer?

---

### Post by lethalfang on 2009-05-08
> **ali780 said:**
> How can I do an inverse search between  okular and kile?
Or alternatively how can I change my dvi viewer in kile from okular to Kdvi viewer?

To do inverse search in okular:
Go to configure okular and change the editor from the default "Kate" to Kile. Shift-click to do inverse search, as supposed to control-click in KDvi. 

To make kdvi your default viewer in kile, go to configure kile --> tool --> build
Replace "okular" with "kdvi" for dvi viewers. 
By the way, I would change the LaTeX command option to --src-specials -interaction=nonstopmode '%source' , so that it will do forward search right.

---

### Post by ub-pir on 2009-12-31
I have done all this and I still cannot get either forward or inverse search to work! I have a 2-button wheel mouse so the Kile manual's instruction to press the middle mouse button does not help... is it possible to reconfigure this somehow? (Pressing left and right mouse button's together doesn't work either)

Or Plan B: Where can I get KDVI? The KDVI website says this is part of the kdegraphics package but it (no longer?) appears to be included...

peter

---

### Post by Khopstick on 2010-01-06
Hi,
I just upgraded to Karmic, and experimented a bit with Kile and Okular. I got it working exactly like KDVI. 
lethalfang's instructions are mostly correct, however there are two more things.
First you have to change the LaTeX build tools from Default to Modern (go to the build tool configuration menu and select Latex, then select Modern in the drop-down menu to the right). 
Secondly, you have to set up your viewer in the ForwardDVI tool, not the ViewDVI! I suspect the view tools do not forward the necessary info to the Viewer.
Alternatively, you could create a new tool, but then make sure you select ForwardDVI for Class in the Advanced tab.
At the moment it does not seem to work for PDFs though. I read in the German ubuntuusers-forum that this feature is oly available in TeXlive 2008, and Karmic still comes with 2007.

Edit: actually I find Okular a bit unstable when used with forward search through Kile, so that I would recommend KDVI for now. (But otherwise Okular seems pretty stable.)

Hope that helps,

Chopstick

---

### Post by sansegundo on 2010-01-26
Thanks a lot for your help, Khopstick. I already have inverse search working in Okular. However, I am still fighting with one problem.  Each time I do an inverse search, a new copy of my LaTeX source file opens in Kile. Have you met this problem? 
I have tried to change this behavior,  in the Okular editor configuration, adding some *--unique* option, or something like that. But the editor command option seems to be fixed in Okular. 
Best regards.

---

### Post by noravanq on 2010-04-16
I also have the problem that any time I do inverse search from okular (pressing shift+mouse) a new instance of Kile is run. 

Does anyone now how to fix this?

Thanks!

---

### Post by noravanq on 2010-04-16
I found a solution to my problem. In Okular go to Settings->Configure Okular->Editor.
It doesn't allow you to edit the Command for kile, so instead choose Custom Text Editor and for the command write

```

kile %f --line %l

```

After doing this, no new kile windows are opened, it just searches in the open source file. The search isn't very accurate though, it is usually off by a couple of lines. I think this is an okular issue.

---

### Post by noravanq on 2010-04-16
My solution above fixed the inverse search, but forward search still opens a new instance of the dvi file. 

Does anyone know how to fix that?

Thanks.

---

### Post by Khopstick on 2010-05-11
I don't have this problem, but I'm using KDVI at the moment... I'm assuming you use the ForwardDVI-Tool for forward search (and not ViewPDF). The --unique flag does not help?

---

### Post by drevicko on 2010-05-14
> **sansegundo said:**
> Thanks a lot for your help, Khopstick. I already have inverse search working in Okular. However, I am still fighting with one problem.  Each time I do an inverse search, a new copy of my LaTeX source file opens in Kile. Have you met this problem? 
I have tried to change this behavior,  in the Okular editor configuration, adding some *--unique* option, or something like that. But the editor command option seems to be fixed in Okular. 
Best regards.

I've had a similar problem. My souce is on a vfat (FAT32) hard disk. Somehow, probably a subversion confusion, I managed to get the folder name in the kile project file (.kilepr) in lower case, like the actual folder (as seen by ubuntu). Inverse search and clicking a latex error opened an upper case version, while the project opened a lower case version - I had the same file in 2 tabs!. 'Save as' revealed the discrepancy, and another inverse search didn't open a third tab.

I solved it by manually changing the case of the folder name for all the files in the .kilepr file (which, by the way, I've had to put on ubuntu's home ext3 file system due to other bugs)

Interestingly, the 'save as' dialog lists all the folders higher in the heirarchy in lower case, as they actually are. Only the last folder (which contains the source files) is listed upper case.

Thanks noravanq - your tip finally got inverse search from okular working (:

Now, I wonder whats up with forward search?? A new okular window every time. Doesn't jump to the correct page in the document.

---

### Post by drevicko on 2010-05-14
Update: 
Okular will jump to the right document section if you invoke it like this:

 [INDENT] okular --unique test.dvi#src:33test.tex
  okular --unique test-main.dvi#src:33test-intro.tex
[/INDENT]
The %target macro in Kile's forwardDVI options produces output in the right form except with a space between the line number and file, which breaks it into two arguments and okular dies. (in fact, I had 3 since there's a space in the path to my directory).

So I used quotes around '%target', except then the # turns into %26 and okular dies.

Then I hit another problem: okular is run in the latex source code directory, and prepends the path to it's arguments: one of my 3 arguments above also had the path repeated!

At this point I nearly gave up, but stumbled across Juerg Wullschleger's post on May 28 09 [here]("http://ubuntuforums.org/archive/index.php/t-1134500.html"). He wrote a perl script to get xdvi working (which, by the way, isn't in lucid ubuntu yet, nor kdvi). A little editing of his script and I came up with the one below, which is working for me! Yay! Way too much time wasted on this!

I put the script in a folder somewhere, used chmod to make it executable and put it's full path as a new forwardDVI configuration:
Settings -> configure kile -> Build -> forwardDVI  then:
[LIST=1]
[*]"new..." button on the right
[*] give it a name, perhaps "My Okular"
[*] put the full path to your perl script as the command (don't forget to escape==[put backslash in front of] any spaces)
[*] put '%target' as Options (the single quotes are important: the script gets it all as one argument that way, otherwise it's broken up at spaces, one of which Kile puts in there for you)
[/LIST]

Don't forget to setup inverse search from Okular: Settings -> Configure Okular .. -> Editor -> editor dropdown: "custom text editor", command: "kile %f --line %l" 
And set up Kile to tell LaTeX to add source info: Settings -> configure kile -> Build -> LaTeX -> "Modern" in the dropdown


```
#!/usr/bin/perl
# kile2okular. (c) Ian Wood, 2010
# based on:
# kile2xdvi. (c) Juerg Wullschleger, 2009

if($ARGV[0] =~ m/file:(.*)#src:(\S*) (\S*)/){
$dviFile = $1;
$line = $2;
$sourceFile = $3;
$sourcePos = '--unique "'.$line.' '.$sourceFile.'"';
if($dviFile =~ m|.*/([^/]*.dvi)|){
$dviFile = $1;
}else{
print 'usage1: kile2xdvi <dvifile> or kile2xdvi "file:<dvifile>#src:<line> <sourcefile>"'."\n";
exit;
}
}else{
if((!$ARGV[0]) || ($ARGV[0] == "--help") || ($ARGV[0] == "-h")){
print 'usage2: kile2xdvi <dvifile> or kile2xdvi "file:<dvifile>#src:<line> <sourcefile>"'."\n";
exit;
}
$dviFile = $ARGV[0];
$sourcePos = '';
}
if (!(-e $dviFile)){
print "$dviFile: No such file.\n";
exit -1;
}

`okular --unique "$dviFile#src:$line$sourceFile"\n`;
exit;
```

---

### Post by yoni_m on 2010-09-16
You can read this post
[http://ubuntuforums.org/showthread.php?t=1134500&page=3](http://ubuntuforums.org/showthread.php?t=1134500&page=3)
for a solution the works for me.

---

### Post by ItalOz on 2010-11-27
I could not find, for some reason KDVI in the repositories, so I went for the solution of post #4 with Okular and it worked straight away

Thanks

By the way where is KDVI?

---

### Post by ADK1 on 2011-01-05
I've done everything that I've read here and I still can't get forward or inverse search working at all; nothing happens when I shift+left click in Okular, and ditto in Kile (the documentation doesn't even describe *exactly* how perform inverse search).

Is there anyone who can describe, step by step, how I might be able to get this working? It seems like an extremely useful feature. If I can get it working on my machine I will gladly write a detailed step by step guide on the matter, and submit it to whoever's in charge of documentation. That includes matters like preventing a new window from popping up, making sure the destination line in the other document is correct, etc. I'd gladly write such a document if I could figure the steps out.

Any help is appreciated. Thanks,
A

---

### Post by turiontzukosson on 2011-04-18
I tried it with Kile 2.0.85 and Texlive 2009 in an up-to-date Kubuntu with Okular 0.11.2 and it still doesn't work with PDF inverse search. Are there any hints why?

DVI inverse search however works with okular.

---

### Post by quickk on 2011-04-20
I have the same problem with okular and kile on my work desktop (Kubuntu 10.10).  I can't get the inverse search working with pdf files.  When I left click, nothing happens.

Oddly enough, I have another machine with linux Mint 10 KDE, and for this machine, inverse search works fine!   If I figure anything out, I'll post it here.

---

