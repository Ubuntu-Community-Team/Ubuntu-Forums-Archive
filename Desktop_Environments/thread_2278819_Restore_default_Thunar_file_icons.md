---
title: "Restore default Thunar file icons?"
date: 2015-05-19
forum: Desktop Environments
---

### Post by amanchesterman on 2015-05-19
I'm running Xubuntu 14.04.2 LTS and I use LibreOffice as my main office suite. However, because LO does not always reproduce correctly the layout of complex .docx documents that I am sent, I recently installed WPS/Kingsoft Office as well. (I downloaded the .deb archive from the Kingsoft website and installed it using the Software Center.)

When I installed it, it immediately set itself as the default office suite for opening .doc, .docx, .xls, .ppt files etc., as such packages usually do. No matter: I have reset the defaults in Thunderbird and Thunar and the default program is now LibreOffice once again. Everything works fine, and I can use Kingsoft if I need to.

My problem is that when Kingsoft installed, it associated its own icons with the .doc, .docx etc. file types and these still display in Thunar. I find them unattractive and I would like to revert to the LibreOffice icons instead.

So far I have:
- looked on the internet and in this forum and not found a solution;
- reset the XFCE Greybird theme and the XFCE icons using Menu > Appearance > Icons and restarted the machine;
- checked that LibreOffice is the default application to open these file types in Menu > All > MIME type editor.

Please note that:
- in the MIME type editor, although LibreOffice is set as the correct application, the **icon** for each file type is the Kingsoft icon;
- the same Kingsoft icons are shown in Thunar, although double-clicking the files in Thunar opens them correctly with LibreOffice;
- this is a question about **file** icons in Thunar (there are other threads about folder icons, with which I have no problem).

Very grateful for any advice or instructions you can give me. I don't particularly want to uninstall Kingsoft Office, since it seems to work well and is a useful addition to my machine, but I would like to be rid of its file icons!

---

### Post by Dennis N on 2015-05-19
@amanchesterman,

I had my LibreOffice Writer documents showing with text file icons in Thunar. I used the method described on this web page to use the LibreOffice Writer icon instead. From what I gather, these user settings override any other settings that exist. So far it has been so.

[http://unix.stackexchange.com/questions/23776/how-to-change-a-file-type-icon-in-xfce-thunar](http://unix.stackexchange.com/questions/23776/how-to-change-a-file-type-icon-in-xfce-thunar)

---

### Post by vasa1 on 2015-05-19
That's a very nice link. I'll try the steps suggested in there to deal with a couple of icon issues I have because I think what's posted there is quite generic and probably not limited to Xfce and Thunar.

---

### Post by Dennis N on 2015-05-20
> **vasa1 said:**
> That's a very nice link. I'll try the steps suggested in there to deal with a couple of icon issues I have because I think what's posted there is quite generic and probably not limited to Xfce and Thunar.

You are right. I have used it with Lubuntu. The steps worked exactly the same.

---

### Post by amanchesterman on 2015-05-20
Hi Dennis N, many thanks for your quick reply and for posting the link -- which, as vasa1 says, looks helpful. Unfortunately those instructions haven't worked for me so far.
I followed them to create a local mimetype definition for .doc files (as an example) but I wasn't sure what to write in it as the name of the icon I want to use. For instance in /usr/share/icons/Humanity/mimes/16/ there's an icon 'application-msword.svg' which I quite like, but in /usr/share/icons/hicolor/16x16/mimetypes/ there's the icon 'application-msword.png' which is the less attractive one currently used by Thunar. In my local mimetype definition file, if I write ```
<icon name="application-msword"/>
``` Thunar continues to use the hicolor icon rather than the Humanity one. Do I also have to specify the file extension (.svg rather than .png)? Or do I put in the full path as the icon name? What did you put in your local definition file?

---

### Post by Bucky Ball on 2015-05-20
> **amanchesterman said:**
> Do I also have to specify the file extension (.svg rather than .png)?

I would imagine yes as without it it doesn't mean much. As for the complete file path, don't know and leaving to those with experience of using this method.

---

### Post by amanchesterman on 2015-05-20
Thank you Bucky Ball, but I have just tried it and adding '.svg' to the icon name makes no difference.

What has me foxed is that in the installed mimetype definition files -- e.g. freedesktop.org.xml, which seems to be what Xfce starts with -- file icon names are written **without** any extensions. I don't know the xml syntax for icon names and I don't understand how Thunar knows which icon to use when there are two or more with the same name but different extensions in the various icon folders! So I thought that if Dennis N can share what is written in his local file, I could maybe just copy that ... ;)

---

### Post by Dennis N on 2015-05-20
Hi amanchesterman, 

I will post that file here with some directions shortly (as soon as I can).

---

### Post by Dennis N on 2015-05-20
Hi amanchesterman;

This is the file I used to change the LibreOffice Writer icon.

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
	<mime-type type="application/vnd.oasis.opendocument.text">
		<comment>OpenDocument Text</comment>
		<icon name="libreoffice-writer"/>
		<glob pattern="*.odt"/>
		<magic>
			<match value="PK\003\004" type="string" offset="0">
				<match value="mimetype" type="string" offset="30">
					<match value="application/vnd.oasis.opendocument.text" type="string" offset="38"/>
				</match>
			</match>
		</magic>
	</mime-type>
</mime-info>


```This file was saved as odt-example.xml in ~/.local/share/mime/packages. Create the mime and packages directories if necessary. 

After saving the file, cd to ~/.local/share/mime and in the terminal run the command update-mime-database $PWD

I believe Xubuntu changed icons immediately; if it doesn't, log out and log in again.  

To get the correct name to use in the <icon name= >, I looked in my icon theme's apps subdirectory for the icon I wanted, and dropped the extension.
 
Here are before and after images of my system's file icon for files of this mime type. The original is used in Faenza (my icon theme) for various mime types regardless of application. I specifically wanted an icon representing LibreOffice writer.   

[ATTACH=CONFIG]262095[/ATTACH][ATTACH=CONFIG]262094[/ATTACH]

Before and After.

---

### Post by amanchesterman on 2015-05-20
Dennis N, you're a star! Thank you very much for such a full and helpful reply.

It hasn't solved my problem but I think it will help me considerably to work out a solution.

The clue is your statement: "To get the correct name to use in the <icon name= >, I looked in  my icon theme's apps subdirectory for the icon I wanted, and dropped the  extension."
On my machine, the icon theme I am using is Elementary XFCE Dark, and that doesn't have an apps subdirectory. It only has icons for the Xfce panel. 

I have tried changing the icon theme to Humanity which, as I said above, does have an acceptable icon in its mimes subdirectory (though not in its apps subdirectory). But that doesn't change the icon displayed in Thunar, and I think that's probably because (as explained earlier) on my machine there are two icons with the same name, albeit with different file extensions. My guess is that in such circumstances, Thunar prefers the icon in the hicolor theme to the icon in the Humanity theme -- and that's because hicolor is the default icon set for Xfce.

In other words, the WPS/Kingsoft installation hasn't just added its own icons to those available in the default theme, which is how LibreOffice seems to operate; rather, it appears to have replaced some of the icons in the default hicolor theme -- so that when Thunar goes to the 'default' icons it now finds the Kingsoft ones instead of the originals.

The important clue you gave me is that the 'icon name' has no file extension in the xml definition. That's really helpful because it reveals that on my system Thunar is having to resolve the ambiguity of two icons with the same name. That must be why the proposed solution isn't working.

At the moment I'm thinking of uninstalling the hicolor theme completely and then reinstalling it from scratch. Of course if I ever re-install the Kingsoft office suite I will face this problem again, but since I don't intend to use it much that's not highly probable.

Unless anyone has alternative solutions to suggest?

---

### Post by Dennis N on 2015-05-20
> On my machine, the icon theme I am using is Elementary XFCE Dark, and that doesn't have an apps subdirectory. It only has icons for the Xfce panel. 
elementary-xfce-dark is not a complete theme. It just has extra icons for use on a dark panel. It depends on elementary-xfce for the rest of the icons. We know this from the index.theme file inside elementary-xfce-dark, which has at the top:
```
[Icon Theme]
Name=elementary Xfce dark
Comment=Addon for dark panels
Inherits=elementary-xfce

```
Inherits=elementary-xfce means the rest of the icons come from elementary-xfce, which does have an apps directory inside to look at. In there is libreoffice-writer.png*, so you would put libreoffice-writer in <icon name= >, giving <icon name="libreoffice-writer"/> which is the same as in the file I posted. _You most likely should be able to use the file just as it is without making any changes_. That code is independent of what theme you are using.

*actually a link, but you can use this name since it points to an image file.

---

### Post by Dennis N on 2015-05-20
I switched my icon theme to elementary-xfce-dark, and the file works correctly as is. The file icon in Thunar that I get is indeed the libreoffice-writer icon for elementary-xfce. Here is the result I get:

[ATTACH=CONFIG]262098[/ATTACH]

Hmmm...looks better than my Faenza icon.

---

### Post by amanchesterman on 2015-05-21
Dennis N, thank you for your continuing efforts to help, and your explanations.

I have followed your advice with a view to making Thunar display the libreoffice-writer icon for '.doc' files. (I thought I'd start with them and then go on to the other ones.) I copied your xml definition file and amended it only by substituting "application/msword" whenever your file has "application/vnd.oasis.opendocument.text" and replacing the glob pattern "*.odt" with the pattern "*.doc". I then updated the mime database and it created (as expected) an xml file which clearly associates the libreoffice-writer icon with the '.doc' filetype.

However that hasn't changed the display in Thunar.

Digging into the system, however, I found in the folder /usr/share/mime/ a file called 'aliases'. Looking at the content I found the following line:
```
application/msword application/wps-office.doc
```
The content is just a list of lines like that, with the name of one file type followed by another, two on each line. I don't really understand what it does but I guess that it tells the system that the second name is the alias of the first. So on my machine, when Thunar encounters a '.doc' file, it recognises that as an 'application/msword' type of file ('cos that's the output I get when I ask it) -- but then the 'aliases' file tells it to treat that as an 'application/wps-office.doc' type of file, with the result that it goes and finds a different icon.

So I'm wondering about trying to edit the 'aliases' file. However I'm reluctant to mess with it because I don't want to break the system. Can you advise on this? Do you know whether the 'aliases' file is relevant to my problem?

---

### Post by Dennis N on 2015-05-21
The link below explains the mime database, and has an explanation of the <MIME>/aliases file. I would leave it alone. Actually, the FIRST entry in each line is the alias of the second entry (the mime type) so in mine, there are lots of aliases mapped to application/msword (mime type).

[https://help.gnome.org/admin//system-admin-guide/2.32/mimetypes-database.html.en](https://help.gnome.org/admin//system-admin-guide/2.32/mimetypes-database.html.en)

I believe the system (Thunar) doesn't actually use the extension to determine the mime type (but some applications may use extensions for their own purposes) -- instead, the OS examines the file internally. The globs, magic, and alias files in the mime database help with that.

A test that an extension isn't needed:

test.odt and test2 were both made with LibreOffice writer as odt files. Even without the extension, the mime type is known. 

```
dmn@Sydney:~/Desktop$ file --mime-type test.odt
test.odt: application/vnd.oasis.opendocument.text
dmn@Sydney:~/Desktop$ file --mime-type test2
test2: application/vnd.oasis.opendocument.text


```

I made a 2 .doc files, one with no extension and tried that:

```
dmn@Sydney:~/work/LO$ file --mime-type sample-file-1.doc
sample-file-1.doc: application/msword
dmn@Sydney:~/work/LO$ file --mime-type sample-file-2
sample-file-2: application/msword

```

Maybe you need to go through the steps outlined in the article with application/ms-word? That's what I did when I made a new file icon for .xml files. When I have more time, I'll look into using the L.O. icon for .doc files. Right now, they have this icon (on two files, that I made for the test):

[ATTACH=CONFIG]262108[/ATTACH]

---

### Post by Dennis N on 2015-05-21
A reference on icon themes and how they work that contains much useful information for study:

[Icon Theme Specification]("https://developer.gnome.org/icon-theme-spec/")

---

### Post by Dennis N on 2015-05-21
Hi amanchesterman;

This code changes .doc file icons in Thunar to LibreOffice Writer icon. I saved it as doc-example.xml in the same directory as the previous file, and updated the mime database. 
Note: There were 2 mime type declarations for <application/msword>. The one I used was in freedesktop.org.xml starting at line 3362.

The final result is this:
```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
	<mime-type type="application/msword">
		<comment>Word document</comment>
		<sub-class-of type="application/x-ole-storage"/>
		<icon name="libreoffice-writer"/>
		<magic priority="60">
			<match value="\x31\xbe\x00\x00" type="string" offset="0"/>
			<match value="PO^Q`" type="string" offset="0"/>
			<match value="\376\067\0\043" type="string" offset="0"/>
			<match value="\333\245-\0\0\0" type="string" offset="0"/>
			<match value="MSWordDoc" type="string" offset="2112"/>
			<match value="MSWordDoc" type="string" offset="2108"/>
			<match value="Microsoft Word document data" type="string" offset="2112"/>
			<match value="bjbj" type="string" offset="546"/>
			<match value="jbjb" type="string" offset="546"/>
		</magic>
		<glob pattern="*.doc"/>
		<alias type="application/vnd.ms-word"/>
		<alias type="application/x-msword"/>
	</mime-type>
</mime-info>

```
and it works. Here is the LibreOffice Writer Faenza icon (my theme) associated with an msword file (.doc). Previous icon is in post #14.
[ATTACH=CONFIG]262112[/ATTACH]

---

### Post by amanchesterman on 2015-05-22
Hi again Dennis N.

Thank you very much for your continuing efforts to help! I really appreciate your patience and the helpful explanations you give as we proceed. I'll respond here to a number of points you have made.

First, in your post #14, you remind me of the need to follow the instructions in the original online tutorial. In fact I did that, but I realise I could have said that more explicitly in my post #5. So (in brief):
- I created a short document and saved it as 'test.doc'
- the system identified it as mimetype 'application/msword'
- I copied that definition for that mimetype from /usr/share/mime/packages/freedesktop.org.xml
- I amended the definition to change the icon name, created the local definition file and updated the mime database
... all as instructed in the tutorial.

Second, in relation to your post #16, I clearly have a different version of freedesktop.org.xml. In mine, the definition of the type 'application/msword' begins at line 3585.

Third, I have just copied and used the code you posted in #16 and it has not worked. For clarity, this is what I did:
- deleted the definition files in ~/.local/share/mime and restarted my machine
- copied your code into a new file 'doc-example.xml', saved it in ~/.local/share/mime/packages and updated the mime database
- checked that it had created a file 'msword.xml' in ~/.local/share/mime/application and checked that the content of that file had the correct icon defined
- restarted the machine

Finally I'm not entirely convinced by your suggestion in post #14 that the 'aliases' file is irrelevant. I haven't yet had the time to read the link you gave, but if -- as you say -- the first entry is the alias of the second, then on my system it is saying that the type 'application/msword' is just another way of describing (= is an alias of) the type 'application/wps-office.doc'. It also says, on another line, that 'zz-application/zz-winassoc-doc' is an alias of 'application/msword', but those are the only two mentions of 'application/msword' in that file. So I still wonder whether my system may be being misled by the reference to wps-office. I can't think of any other explanation as the moment of why definition files that obviously work so well on your system don't have the same effect on mine.

Anyway it's 8:15 am here at present and I have to get on with my day. I'll be out for much of it but I'll hope to have another look at this tonight. Thank you again for your assistance!

---

### Post by Dennis N on 2015-05-22
Wow - sorry you are having so much trouble. I am at a loss. As to the alias file, I rely on what I read at the linked documentation:
Quote:
> "For each line in this file there are two fields: the first field is the alias name, and the second field is the MIME type."

---

