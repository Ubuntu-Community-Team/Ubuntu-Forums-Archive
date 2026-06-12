---
title: "converting .lit files to PDFs"
date: 2009-01-29
forum: Education &amp; Science
---

### Post by scragar on 2009-01-29
I found this a bit annoying, but the conventional method of converting .lit files to PDFs is to use open office or abiword and copy and paste the contents from firefox, then choose save as PDF or export to PDF. As a result I wrote this shell script, it has two dependencies, convlit and htmldoc
```
sudo apt-get install convlit htmldoc
```
Then you want to download the attachment(to your home folders a good idea), drop into a terminal and run:
```
chmod +x lit2pdf.txt
sudo mv lit2pdf.txt /usr/bin/lit2pdf
```
Then find any .lit file you want, right click it, and open it with "lit2pdf", using the custom command box. When it is done you will be told how many files were extracted and asked if you wish to delete the .lit file now.

Let me know if you get any errors etc.

---

### Post by graphius on 2009-02-12
A few things, first, you need to sudo apt-get install convlit **htmldoc**

then sudo mv lit2pdf.txt **/usr/bin/lit2pdf**

I ran the script on a few .lit files and the dialog comes up saying 0 files were created, then it gives me the option to delete the lit file

Any suggestions?

PS thanks for the script

---

### Post by sharon.gmc on 2009-02-13
Is there any other simpler way to do it?  I am not good with scripts.

---

### Post by scragar on 2009-02-13
> **graphius said:**
> A few things, first, you need to sudo apt-get install convlit **htmldoc**

then sudo mv lit2pdf.txt **/usr/bin/lit2pdf**

I ran the script on a few .lit files and the dialog comes up saying 0 files were created, then it gives me the option to delete the lit file

Any suggestions?

PS thanks for the script

That's strange, try this edit:
```
#!/bin/bash

CONFDIR=~/.lit2pdf
CONVLIT=clit
MODE=continuous
DEBUGMODE=1      ## 1 = on, 0 = off

### please don't go complaining if you edit after here and break it.

FILE=$1  ## basic init
MSGBOX=$(which gxmessage) || MSGBOX=xmessage
NUM=0

SUBDIR="$CONFDIR/`basename "$FILE"`" ## generate a sub dir path, more or less anyway :p

function DebugMsg {
	if [ $DEBUGMODE == 1 ]; then
		$MSGBOX $1
	fi
}


if [ -f "$FILE" ]; then ## we are working with a valid input file
	mkdir -p "$CONFDIR" ## make the config dir if it doesn't exist

	while [ ! mkdir "$SUBDIR-$NUM" ]; do ## generate a unique sub dir
		NUM=`expr $NUM + 1`
	done;

	SUBDIR="$SUBDIR-$NUM" ## and a bit more config here, now we know our dir
	NUM=0

	DebugMsg "$SUBDIR"

	$CONVLIT "$FILE" "$SUBDIR/" ## extract the lit file

	DebugMsg "`ls $SUBDIR`"

	for htm in $SUBDIR/*.htm $SUBDIR/*.html; do ## for all the HTML files
		if [ -f "$htm" ]; then ## double check it exists

			htmldoc --$MODE -f "./`basename "$htm"`.pdf" "$htm" ## convert it to PDF
			NUM=`expr $NUM + 1` ## increase counter
		fi
	done ## end loop

	rm -rf "$SUBDIR" ## remove our little unique dir now

	## let the user know we are done, and if they click "delete" we remove the input file as well.
	$MSGBOX -buttons "Delete:0,Leave:1" "$NUM file(s) created."$'\n'"Delete .lit file now?" && rm $FILE;

fi
```
And let me know what the first two messageboxes say.

---

### Post by statmonkey on 2009-04-28
I didn't post the original question but am seeing the same thing.  A couple of points. 

1. when I attempted to sudo apt-get install *convlit heredoc * I get the complaint that convlit is the lastest already and apt is unable to find heredoc.

2. Whether I run the initial downloaded script or the new one you posted above I get the same results from X Message:

0 file(s) created.
Delete .lit file now?

I thought at first it might be permission related and made sure the script is owned by me.  But no change, same result.  

So I then copied the script to a folder I use as a catchall to run tests in my home and attempted to run the script from the command line as shown below with the results.  It looks to me as convlit is choking and perhaps this is about heredoc.  I don't know this software and am just about to start Googling.  Initially I assumed you meant htmldoc.  Maybe this is wrong.


I hope this helps, this is a great idea, I know Calibre will open Lit files but I really like to keep as little as possible on my netbook and want to reduce apps wherever I can this script would help in that.

```
stat@stat:~/Music$ ./lit2pdf.txt To\ Kill\ a\ Mockingbird.lit 
./lit2pdf.txt: line 19: [: mkdir: unary operator expected
+---[ ConvertLIT (Version 1.8) ]---------------[ Copyright (c) 2002,2003 ]---
ConvertLIT comes with ABSOLUTELY NO WARRANTY; for details
see the COPYING file or visit "http://www.gnu.org/license/gpl.html". 
This is free software, and you are welcome to redistribute it under 
certain conditions.  See the GPL license for details.
LIT INFORMATION.........
DRM         =  1    
Timestamp   =  4b302d20 
Creator     =  00000000 
Language    =  00000409 
Writing out "To_Kill_A_Mockingbird" as "To Kill A Mockingbird.htm" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/To Kill A Mockingbird.htm".

Writing out "RW_~Cover01" as "~Cover01.jpg" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/~Cover01.jpg".

Writing out "RW_~Cover02" as "~Cover02.jpg" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/~Cover02.jpg".

Writing out "RW_~Cover03" as "~Cover03.jpg" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/~Cover03.jpg".

Writing out "RW_~Cover04" as "~Cover04.jpg" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/~Cover04.jpg".

Writing out "RW_~Cover05" as "~Cover05.jpg" ...
Successfully written to "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/~Cover05.jpg".

Exploded "To Kill a Mockingbird.lit" into "/home/stat/.lit2pdf/To Kill a Mockingbird.lit-0/".
```

---

### Post by scragar on 2009-04-28
Yeah, OP updated, my mistake writing heredoc, it's **htmldoc**, dunno what made me write heredoc.

It's not working for you because you didn't install htmldoc, sorry for having written the wrong thing.

---

### Post by statmonkey on 2009-04-30
Well, I certainly have done something incorrect but not sure what.  I have (and always had htmldoc (version 1.8.27) and convlit.
1. I downloaded your script again to my home directory - scripts
2. chmod +x lit2pdf.txt to make it exectuable
3. sudo mv lit2pdf.txt /usr/bin/lit2bin as shown above in your instructions.  
4. Then I select the lit file I want to convert and select the command I want to use in custom command.  Your instructions say to use lit2pdf to convert the file but that seems counter intuitive since in step 3 we changed the name to lit2bin as you instructed above so I chose lit2bin from the usr/bin folder thinking that is what you meant. I also changed the file to lit2pdf but same result so I don't think it has anything to do with the name of the file and probably nothing to do with where it is as long as it is executable.

Regardless of whether I use that or just use a copy of your script that I downloaded and left in the same folder to test with (after making executable) I get the same results as already noted.  Pretty sure I am missing something and just not sure what it is.  This would seem relatively straight forward and to be honest at this point it is less about using this tool than trying to figure out what I did wrong or am doing wrong.

---

### Post by qwerty1212 on 2009-05-27
couldn't get this to work so I made this script
```

#!/bin/bash
FILE="$1"
NAME="${FILE%.*}"

if [ -f "$FILE" ]; then # check that input file exists
	clit "$FILE" "$NAME/" # convert lit to htm
	for HTM in "$NAME"/*.htm; do
		htmldoc --continuous --header ... --footer ..1 -f "$NAME.pdf" "$HTM" # convert htm to pdf
	done
	rm -rf "$NAME/" # remove temporary files
fi

```

---

### Post by marseille on 2009-07-04
[COLOR="Purple"]i just used scragar's script successfully but the thread was a little confusing. anyway it took all of 5 minutes or less to set this up and i just glanced over my newly converted `lit to pdf' book doing this:[/COLOR]


**in terminal run:**

> $ sudo apt-get install convlit htmldoc

download [lit2pdf.txt]("http://ubuntuforums.org/attachment.php?attachmentid=101362&d=1233210996") (*to home folder*)

**in terminal run:**


> $ chmod +x lit2pdf.txt
$ sudo mv lit2pdf.txt /usr/bin/lit2pdfv


**open .lit file you want to read by:**

* right click .lit file
* open with `lit2pdf' (*using custom command box*)

*says how many files were extracted and asks to delete .lit file*

* hit `**delete**' button (*converts .lit file to pdf automatically*)

---

### Post by Maybelline on 2009-07-17
Hey, great script.  Works great, save for one thing.  I think you could/should change the following line:
```
for htm in $SUBDIR/*.htm $SUBDIR/*.html; do ## for all the HTML files
```

to have quotes like this:
```
for htm in "$SUBDIR"/*.htm "$SUBDIR"/*.html; do ## for all the HTML files
```

It fixes a problem of spaces in the folder name.

Before calling htmldoc, I added this line, to change the title of the resulting PDF.  It's ugly & hacky, but it gets something better than the 1st line of text as the PDF title.

```
sed -i "s,\<title\>.*\<,title\>`basename "$htm"`\<\/,g" "$htm"
```

I also added ```
--header /t
``` to the htmldoc line, so that I get page numbers & a title on the top of each page.

---

### Post by scragar on 2009-07-17
> **Maybelline said:**
> Hey, great script.  Works great, save for one thing.  I think you could/should change the following line:
```
for htm in $SUBDIR/*.htm $SUBDIR/*.html; do ## for all the HTML files
```

to have quotes like this:
```
for htm in "$SUBDIR"/*.htm "$SUBDIR"/*.html; do ## for all the HTML files
```

It fixes a problem of spaces in the folder name.

Before calling htmldoc, I added this line, to change the title of the resulting PDF.  It's ugly & hacky, but it gets something better than the 1st line of text as the PDF title.

```
sed -i "s,\<title\>.*\<,title\>`basename "$htm"`\<\/,g" "$htm"
```

I also added ```
--header /t
``` to the htmldoc line, so that I get page numbers & a title on the top of each page.

Thanks for those tips, I've made a few changes and put it into a .deb in case anyone wants to try it(would be easier to install and remove or whatever).

MD5: 15f150a882746188710d331c32fb1742

I have no idea why it's so large for an installer, the contents are really small in comparison.

---

### Post by Clancy_s on 2009-07-22
Thanks, I'll give the deb a go.

---

### Post by pooja on 2009-08-04
I've tried the script but it says "0 files converted".
Where did I go wrong?

PS. I also tried downloading the attached *.deb file in post #11 - still doesn't work

---

### Post by pooja on 2009-08-04
> **marseille said:**
> [COLOR="Purple"]i just used scragar's script successfully but the thread was a little confusing. anyway it took all of 5 minutes or less to set this up and i just glanced over my newly converted `lit to pdf' book doing this:[/COLOR]


**in terminal run:**



download [lit2pdf.txt]("http://ubuntuforums.org/attachment.php?attachmentid=101362&d=1233210996") (*to home folder*)

**in terminal run:**



**open .lit file you want to read by:**

* right click .lit file
* open with `lit2pdf' (*using custom command box*)

*says how many files were extracted and asks to delete .lit file*

* hit `**delete**' button (*converts .lit file to pdf automatically*)



I did that but it says "0 files converted".
I now see there are 2 scripts:  "lit2pdf" and "lit2pdf**v**"
If I choose the former to open the .lit file I get an error message (see attached pictures).

---

### Post by marseille on 2009-08-06
i went to convert a .lit file to pdf and found the script broke.  i have done some updates -- still on ibex -- since i last used the script so i am wondering if that did it.  any ideas?

ps: i did not install a .deb, used original script

pss: pooja had the right script _[window pop-up]("http://ubuntuforums.org/showpost.php?p=7731024&postcount=13")_ -- but hitting `_[delete]("http://ubuntuforums.org/showpost.php?p=7559876&postcount=9")_' to automatically produce the new PDF file no longer works since the updates.

---

### Post by pooja on 2009-08-07
I managed to open the file!

I installed **ConverLit** then I gave the following command to the Terminal:

[FONT="Courier New"]sudo apt-c [/FONT]

In the Terminal I changed to the directory containing the *.lit file. For example, if the file is called "book.lit" and is saved on the Desktop I would write:

[FONT="Courier New"]cd ~/Desktop[/FONT]

Then I issue this command:

[FONT="Courier New"]clit book.lit myfolder/[/FONT]

This will "explode" the book.lit file inside a folder called "myfolder", on the Desktop.
If you go to the Desktop, you should find that folder (this is so in our example). Open it, you'll see a "book.html" file so open it with Mozilla Firefox. 

Once you're in Mozilla, navigate to [FONT="Courier New"]File > Print[/FONT]. Click on [FONT="Courier New"]Print to file[/FONT]. Choose a location, a name and most importantly, don't forget the extension: it must be [FONT="Courier New"].pdf[/FONT]. In our example, [FONT="Courier New"]book.pdf[/FONT] will be saved on the Desktop. Press [FONT="Courier New"]PRINT[/FONT] and the printing-to-file process should start in seconds. Wait for it to complete and you're done!

---

### Post by pooja on 2009-08-07
@ marseille:

How do I remove the "lit2pdf" and "lit2pdfv" scripts? 
Thank you.

---

### Post by jamadagni on 2009-12-18
> **pooja said:**
> @ marseille:

How do I remove the "lit2pdf" and "lit2pdfv" scripts? 
Thank you.

No big deal, just do sudo rm path-to-lit2pdf path-to-lit2pdfv. You probably placed them in /usr/bin/ so the command you need is:

sudo rm /usr/bin/lit2pdf /usr/bin/lit2pdfv

Please be careful that you type the correct filename so you do not delete some important system file inadvertently. Disclaimer: You are responsible for your actions!

---

### Post by karmila on 2010-08-12
Hi,

I downloaded the deb and succesfully installed lib2pdf. But, i can not make it ran. It always said 'could not find lib2pdf'.

When i ran lib2pdf in terminal, it said '/usr/bin/lit2pdf: Permission denied'.

Do i need change permission for this? And How? I am new to linux.

Thanks.

---

### Post by souravdefermat on 2010-09-26
thanks guys

---

