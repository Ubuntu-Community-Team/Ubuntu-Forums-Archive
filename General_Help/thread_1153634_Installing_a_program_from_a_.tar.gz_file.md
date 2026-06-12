---
title: "Installing a program from a .tar.gz file"
date: 2009-05-08
forum: General Help
---

### Post by polskimoose on 2009-05-08
i downloaded something that came as a .tar.gz

how do i work with that

i tried typing in: tar xvj4 name_of_file.tar.gz
but it didnt work

---

### Post by sgosnell on 2009-05-09
Open Nautilus, right-click on the file, and select Open with Archive Manager.  Select Extract, and where you want the files to go.  Once extracted, you will have to compile the package.  You need build-essential installed to do this.  Once it is installed, you need to find out what files are available.  If there is one named configure, open a terminal, navigate to the folder, and type "./configure".  Once that runs, type "make".  Once you get a good compile, type "sudo make install".

If there is no configure file, you may need to run make directly, but there may be another setup file available.  You need to read the docs for the app to find out exactly how to get it done.  Different developers do things differently.  There is no hard standard.

---

### Post by Tipped OuT on 2009-05-09
*sigh* Right click, extract, install.

---

### Post by JK3mp on 2009-05-09
> **Tipped OuT said:**
> *sigh* Right click, extract, install.

Gee, your specific. Build essential is required but u likely already have it. Just navigate to the directory in terminal, Run : tar -zxvf file.tar.gz . Should show contents of file's being extracted. Then you can cat README file to see how to install. Generally its just.
"./configure" then "make" then "make install" . Pretty guided from there. Or you can take the nautilus route and open it in the GUI but you'll have to come back to run config and install anyways in terminal... gl :)

---

### Post by Tipped OuT on 2009-05-09
> **JK3mp said:**
> Gee, your specific. Build essential is required but u likely already have it. Just navigate to the directory in terminal, Run : tar -zxvf file.tar.gz . Should show contents of file's being extracted. Then you can cat README file to see how to install. Generally its just.
"./configure" then "make" then "make install" . Pretty guided from there. Or you can take the nautilus route and open it in the GUI but you'll have to come back to run config and install anyways in terminal... gl :)

That's what the "install" refers to, too lazy right now to explain, leave me alone. :evil::lolflag:

---

### Post by soro2005 on 2009-05-09
Well, if it's a python script or some java stuff or just a cheap batch script, he won't have to compile anything. If it's a binary installer, he also won't need to compile. The only decent answer to this question is: It depends. You don't expect that the contents of the zip files you download for your Windows box are all the same. :popcorn:

---

### Post by m4lte on 2009-05-09
You might want to have a look at this How To: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by meeples on 2009-05-09
im trying to install teeworlds 0.5.1 from source but its really annoying.

it didnt come with any install instruction and whenever i do ```
./configure
```

i get
```
bash: ./configure: No such file or directory
```

i would normally use the repo but the version there is too old to even consider.

---

### Post by meeples on 2009-05-09
:O:O its ok,

ive just noticed they have updated it in the repo

LOL

i hadnt checked recently.

sorry:P

---

### Post by sgosnell on 2009-05-09
The result you're getting indicates that there is no configure file in the archive.  Some developers provide it, some don't.  If ./configure doesn't work, try make.  You have to check the extracted files and see what is there.  The first step should always be to read the docs.  That's how hackers learn to manipulate things - they RTFM, completely, and that tells them most of what they need to know.

Having a .deb file is always easier, though.  :P

---

### Post by polskimoose on 2009-05-09
how/where do i get build essential

---

### Post by oldos2er on 2009-05-09
Run
```
sudo apt-get install build-essential
```
in a terminal.

---

### Post by sgosnell on 2009-05-09
Or open Synaptic, find build-essential in the list, mark it for installation, then click Apply.

---

