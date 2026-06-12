---
title: "File System..."
date: 2011-08-10
forum: Desktop Environments
---

### Post by michaell4 on 2011-08-10
Hi,

I've been meaning to ask about this for a while.

When ever I extract a file from a .tar or whatever, it isn't detected.
I notice this mainly when i'm using xampp. I copy zip up all my files on one computer, load ubuntu on another, extract the files to the web folder (htdocs) and then I get nothing. However, when I manually create the files directly on my computer as opposed to extracting them, they appear.

Is there something I need to do in order to have these files appear? Is there some sort of file system refresh? Or am I being a complete idiot?

BTW im pretty much a linux beginner.

Thanks for any help.

Michael

---

### Post by Frogs Hair on 2011-08-10
The only time I have had problems extracting from an archive is if the package is corrupt in some way . Once in a while I get this behavior from theme packages , but not on any regular basis.

---

### Post by michaell4 on 2011-08-11
the package is perfectly fine. when extracted on windows its contents are picked up by xampp. 
It seems like the files aren't being detected at somepoint but when I go to the location of files that appear to be missing; they are there, I can open them and edit them. 

Like I said in my previous post if I manually create the file by going to it's location and create a file with the exact same name (obviously after removing or editing the file name of the existing file) it is detected. 

I'm still no further forward :(

---

### Post by mcduck on 2011-08-11
Check the ownership and permissions of the extracted files, if the files come from a Windows system or a .zip archive both ownership and permissions might be wrong.

---

### Post by michaell4 on 2011-08-11
> **mcduck said:**
> Check the ownership and permissions of the extracted files, if the files come from a Windows system or a .zip archive both ownership and permissions might be wrong.

Yeah, I was just about to ask if that could be the problem lol.

Another thing, I'm using the right click > extract here method, could that be the problem? Should I be using the terminal?

Cheers

---

### Post by mcduck on 2011-08-11
> **michaell4 said:**
> Yeah, I was just about to ask if that could be the problem lol.

Another thing, I'm using the right click > extract here method, could that be the problem? Should I be using the terminal?

Cheers

no, it makes no difference if you use a command-line tool or a GUI tool, both should extract the archives just fine. Just use which one you are most comfortable with. :)

The permissions tend to be quite important with server applications, even though I can't tell you what exactly is required for XAMPP (I use Ubuntu's own LAMP stack instead) but simply comparing the ownership & permissions of the extracted files with ones that you created and that work should give the answer...

---

