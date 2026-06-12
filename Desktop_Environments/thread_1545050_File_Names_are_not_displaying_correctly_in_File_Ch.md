---
title: "File Names are not displaying correctly in File Chooser when the language is Telugu"
date: 2010-08-03
forum: Desktop Environments
---

### Post by uday060 on 2010-08-03
[SIZE=2]Hi Ubuntu Team,

   Actually i am working on an application in which i want to select the files from a File Chooser where the application language is set to Telugu. But when i want to view the files through the File Chooser, all the names of the files in the system are displaying as boxes. This problem occurs only when i change the language to Telugu.This problem doesn't appear with any other languages. So please direct me towards the solution for this problem.

  Thanks in advance.
           Uday.[/SIZE]

---

### Post by demosthenese on 2010-08-03
Are the fonts installed?

```
sudo apt-get install ttf-indic-fonts
```

---

### Post by uday060 on 2010-08-04
I installed the specified indic fonts, but i didn't get any solution for that. Still the file chooser displaying the folders and file names as boxes. Please suggest me.

---

### Post by demosthenese on 2010-08-04
You may also need to refresh the font cache.

```
fc-cache -f -v
```

---

### Post by uday060 on 2010-08-04
Thank you for your support.
I executed your command and i didn't get any improvement.

I got the follwoing log in my Terminal.

root@dt-corp-einubun8:~# fc-cache -f -v
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 0 fonts, 15 dirs
/usr/share/fonts/truetype/arphic: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/kochi: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/openoffice: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/thai: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-arabeyes: caching, new cache contents: 39 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bengali-fonts: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-bitstream-vera: caching, new cache contents: 10 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 6 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-indic-fonts-core: caching, new cache contents: 11 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-lao: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-malayalam-fonts: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-telugu-fonts: caching, new cache contents: 3 fonts, 0 dirs
/usr/share/fonts/truetype/unfonts: caching, new cache contents: 4 fonts, 0 dirs
/usr/share/fonts/truetype/vlgothic: caching, new cache contents: 2 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/root/.fonts: skipping, no such directory
/var/cache/fontconfig: cleaning cache directory
/root/.fontconfig: not cleaning non-existent cache directory
fc-cache: succeeded


And one more thing, in my application i set the Look and feel of the application to Cross Platform look and feel(Windows Look and Feel). But when i try to run my application with System look and feel the file chooser displaying correctly all the files and folders names in English. The major problem is happening by setting the Look and feel to Cross Platfrom look and feel by the following command.

UIManager.setLookAndFeel(UIManager.getCrossPlatformLookAndFeelClassName());

I have the requirement to support this application in the Cross Platform Look and Feel.
So please suggest me regarding this.

Thanks in Advance.

---

### Post by demosthenese on 2010-08-04
I'm guessing that this is a java program you are coding - which I'm no expert at. I found a blog entry that seems to refer to modifying JFileChooser to work in Bangla. Perhaps you could modify the code shown to work with the Telugu font.

[http://shamsmi.blogspot.com/2008/03/internationalize-swings-jfilechooser-in.html]("http://shamsmi.blogspot.com/2008/03/internationalize-swings-jfilechooser-in.html")

I hope this is relevant.

---

### Post by uday060 on 2010-09-20
Initially my application was installed on the system in English language. When the user changes the application language to some other and whenever he try to open the File Chooser, all the Files and Directories names in the system should be displayed in English only like Desktop, MyDocuments etc and the Folder/File names which are in English language should not get translated to the currently selected language. Actually we are providing the support for 47 languages including telugu. All the 46 languages except telugu are behaving correctly. **But when the language is changed to telugu, the Folder/File names which are created in English(like Desktop, My Documents etc) are displaying as boxes**. I think when the language is changed to telugu, it is trying to translate the system folder/files as well into telugu language.

 The problem exists in both Windows & Ubuntu operating system but not in Mac. This may be a problem at the OS end or may be the problem at Java side. Please confirm and let me know. I dont have the option to upload the screen shot of this scenario to you, otherwise i would upload it to you.

Thanks in advance.

---

