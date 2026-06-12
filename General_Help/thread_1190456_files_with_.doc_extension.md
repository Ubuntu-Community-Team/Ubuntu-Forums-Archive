---
title: "files with .doc extension"
date: 2009-06-17
forum: General Help
---

### Post by monkey186 on 2009-06-17
In xubuntu 9.04 files with .doc extension are treated as 'plain text document' which they surely not. The problem is if i assign openoffice to open them then the same happens to all .txt files that is they also get opened by openoffice.

I.e. i don't seem to find the way to get .txt files to be treated by mousepad and .doc files by openoffice at the same time, it is only one way or another. This is very inconvenient, and certainly never happened in previous releases of xubuntu?

---

### Post by mynameinc on 2009-06-17
Sorry for trolling, post removed.  Not used to helping people.

---

### Post by monkey186 on 2009-06-17
> **mynameinc said:**
> .doc is the Micro$oft Word extension... this is Linux, not Micro$oft Windows...

eh?

---

### Post by aesis05401 on 2009-06-17
File extensions, in this case the .doc extension, are used in the MS world - which I think is what the other poster was referencing in an unhelpful manner. 

Basically, Linux does not use file extensions in the same way.  Instead, there is the 'magic' file located in your /usr/share/file directory.  This lists values that equate a file with a file type - and you can view this file like any other text file.  The entries you see in there are literally the character sequences that identify different types of files to the Linux OS.

The problem you have is that apparently Linux is identifying .doc and plain text as the same files.  I'm not sure of the solution to this, but the file extension system is explained pretty well in the Linux man pages, on wikipedia, and you can view file information through simple command line utils like 'file.'

I'm sure other people who use the .doc format have already solved this problem, though.. 

I just didn't want to leave this thread with only an 'M$ blah blah.. ' troll post in reply to your question.

Good day.

---

### Post by jumbofishmeat on 2009-06-17
@ mynameinc - .doc is a universal file protocol. It's not limited to just microsoft. Rarely anything is these days.

what exactly did you do to set the .doc extension to open in openoffice?

---

### Post by kerry_s on 2009-06-17
> **monkey186 said:**
> In xubuntu 9.04 files with .doc extension are treated as 'plain text document' which they surely not. The problem is if i assign openoffice to open them then the same happens to all .txt files that is they also get opened by openoffice.

I.e. i don't seem to find the way to get .txt files to be treated by mousepad and .doc files by openoffice at the same time, it is only one way or another. This is very inconvenient, and certainly never happened in previous releases of xubuntu?

that's strange, i use abiword on mine and it works fine.

---

### Post by monkey186 on 2009-06-17
> **aesis05401 said:**
> The problem you have is that apparently Linux is identifying .doc and plain text as the same files.

Yep this seems to be what causes the problem.  

> **jumbofishmeat said:**
> what exactly did you do to set the .doc extension to open in openoffice?

I right clicked on it, chose 'open with other application', and in the dialogue chose 'openoffice.org writer' making sure 'use as default for this kind of file' is checked. Which worked, but because 9.04 seems to identify .doc and .txt as files of the same type, now all my .txt documents are also get opened by ooo writer.

---

### Post by WIGGMPk on 2009-06-17
> **jumbofishmeat said:**
> .doc is a universal file protocol.

This extension was developed by Microsoft and requires conversion and API programming calls (which is performed by the programs that support the extension) by all programs that use it, including OpenOffice (except for native Microsoft Office).

So, technically this extension is universally 'supported' but it is definitely not a 'universal file protocol' for word processing applications.

Just an FYI

---

### Post by monkey186 on 2009-06-17
> **kerry_s said:**
> that's strange, i use abiword on mine and it works fine.

Kerry how does your file manager identifies .doc files? Mine (thunar) as 'plain text document' which i think causes the problem:

.

---

### Post by kerry_s on 2009-06-17
as word

---

### Post by monkey186 on 2009-06-17
> **aesis05401 said:**
> I'm sure other people who use the .doc format have already solved this problem, though.. 

i did try a search here on the forum and also google, but don't seem to find anything.... i'm sure though it must have been discussed somewhere as many people use .doc files as well as .txt, i just don't seem to find it!

---

### Post by kerry_s on 2009-06-17
try opening it in oow, then save it under a different name with the .doc extension. it could be the file was converted some time in the past and it's confusing the system.
or 
try the 1 i used to test:
[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ffredrik.hubbe.net%2Fplugger%2Ftest.doc&ei=2q45SoarKYKuswOyqJj-Bg&rct=j&q=test.doc&usg=AFQjCNEwcNYbqKMTZVsfXF0RqbKXHWT0cA&sig2=tu8URj1elh8GFJyaD57Aqw](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ffredrik.hubbe.net%2Fplugger%2Ftest.doc&ei=2q45SoarKYKuswOyqJj-Bg&rct=j&q=test.doc&usg=AFQjCNEwcNYbqKMTZVsfXF0RqbKXHWT0cA&sig2=tu8URj1elh8GFJyaD57Aqw)

---

### Post by monkey186 on 2009-06-17
> **kerry_s said:**
> as word

yeah strange, mine doesn't:-k 

you also using xubuntu 9.04?

---

### Post by kerry_s on 2009-06-17
> **monkey186 said:**
> yeah strange, mine doesn't:-k 

you also using xubuntu 9.04?

debian testing xfce4

---

### Post by mynameinc on 2009-06-17
> **jumbofishmeat said:**
> @ mynameinc - .doc is a universal file protocol. It's not limited to just microsoft. Rarely anything is these days.

what exactly did you do to set the .doc extension to open in openoffice?

Sorry, Wikipedia had me under the impression .doc was a Microsoft-only file.

Closer reading reveals the opposite, though.

EDIT: I am also tired, it is 2317 here.  I probably shouldn't be awake, much less posting on a forum.

---

### Post by monkey186 on 2009-06-17
> **kerry_s said:**
> try opening it in oow, then save it under a different name with the .doc extension. it could be the file was converted some time in the past and it's confusing the system.
or 
try the 1 i used to test:
[http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ffredrik.hubbe.net%2Fplugger%2Ftest.doc&ei=2q45SoarKYKuswOyqJj-Bg&rct=j&q=test.doc&usg=AFQjCNEwcNYbqKMTZVsfXF0RqbKXHWT0cA&sig2=tu8URj1elh8GFJyaD57Aqw](http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Ffredrik.hubbe.net%2Fplugger%2Ftest.doc&ei=2q45SoarKYKuswOyqJj-Bg&rct=j&q=test.doc&usg=AFQjCNEwcNYbqKMTZVsfXF0RqbKXHWT0cA&sig2=tu8URj1elh8GFJyaD57Aqw)

Did try the file from your link, and re-saving it as doc in openoffice, didn't seem to make a difference:

.

---

### Post by monkey186 on 2009-06-17
> **mynameinc said:**
> 
EDIT: I am also tired, it is 2317 here.  I probably shouldn't be awake, much less posting on a forum.

Its 4:23am over here heh..! Maybe my laptop is tired and so playing tricks on me, i should probably switch it off give it some rest.....;)

---

### Post by mynameinc on 2009-06-17
> **monkey186 said:**
> Its 4:23am over here heh..! Maybe my laptop is tired and so playing tricks on me, i should probably switch it off give it some rest.....;)

Are the "ShamWOW" ads aired in the UK?  If so, you could buy a ShamWOW and use it to absorb the problem.  ;P  Once again, sorry for trolling.

---

### Post by monkey186 on 2009-06-17
I'm kind of new to this so getting there veeery slowly;), this is the output of file command

```
oli@cactus:~/Desktop$ file test.doc
test.doc: Microsoft Office Document Microsoft Word Document
oli@cactus:~/Desktop$ 

```

Does this mean that the system identifies the file type correctly, so the problem is with xfce?

---

### Post by kerry_s on 2009-06-18
> **monkey186 said:**
> I'm kind of new to this so getting there veeery slowly;), this is the output of file command

```
oli@cactus:~/Desktop$ file test.doc
test.doc: Microsoft Office Document Microsoft Word Document
oli@cactus:~/Desktop$ 

```

Does this mean that the system identifies the file type correctly, so the problem is with xfce?

try deleting your ~/.local/share/applications
that should set everything back to like the first time you use it.

---

### Post by monkey186 on 2009-06-18
> **kerry_s said:**
> try deleting your ~/.local/share/applications
that should set everything back to like the first time you use it.

Tried it, and even rebooted computer afterwards, still the same problem..:(

---

### Post by monkey186 on 2009-06-18
p.s. in my /ect/mime.types doc extension (as well as dot) is identified correctly with application/msword.. but in desktop/thunar appears as 'plain text document'..

---

### Post by kerry_s on 2009-06-18
i don't know.
if it was me, i would delete every "thunar" folder/file in my home, remove and reinstall thunar.

---

### Post by monkey186 on 2009-06-23
Reinstalling did help. Though i decided not to go back to xubuntu, just put base debian with xfce! 

Have to go learn the new system now. #-o

---

