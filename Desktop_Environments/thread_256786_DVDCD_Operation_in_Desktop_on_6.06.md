---
title: "DVD/CD Operation in Desktop on 6.06"
date: 2006-09-13
forum: Desktop Environments
---

### Post by prioret on 2006-09-13
I think im having problems with automount in gnome. As I am new to this, I'm not sure I understand the expected behavior.  What should happen when I:
1. Insert a movie dvd?
2. Insert a data dvd?
3. Insert a blank dvd?
4. Insert a CD (music)?
5. Insert a data CD?

Should an icon apear on the desktop?
What should it say?
Where does the volume acutally mount incase I need to access it from the terminal?
How should it be ejected?
How do I handle writing to blank media?
What about multipe devices? I have a CD via IDE, and a DVDRW via USB2.

I know its a lot of questions, but I cant seem to figure out what the normal operation is.

Now when I insert a DVD (movie) to the USB2 DVD drive, a icon apears on the Desktop called DVD-ROM Disk. When I click on it to open I get a desktop floder with a heading: "CD/DVD Creator" I dont think this is correct. I would expect to see the data files, and perhaps something like VLC start up.

I get the same thing when inserting a Data DVD.

When in insert a Audio CD, I get a Audio Disk Icon on the desktop, and Sound Juicer starts. That seems correct.

When I insert a Data I get a Icon on the desktop with the CDs Name, and the DVD Recorder - File Browser comes up. That doesnt seem quite right (its not a CDR or CDRW)

I know its a lot of questions!

Thanks.
Tom

---

### Post by meng on 2006-09-13
> **prioret said:**
> I think im having problems with automount in gnome. As I am new to this, I'm not sure I understand the expected behavior.  What should happen when I:
1. Insert a movie dvd?
2. Insert a data dvd?
3. Insert a blank dvd?
4. Insert a CD (music)?
5. Insert a data CD?

Should an icon apear on the desktop?
What should it say?
Where does the volume acutally mount incase I need to access it from the terminal?
How should it be ejected?
How do I handle writing to blank media?
What about multipe devices? I have a CD via IDE, and a DVDRW via USB2.

I know its a lot of questions, but I cant seem to figure out what the normal operation is.

Now when I insert a DVD (movie) to the USB2 DVD drive, a icon apears on the Desktop called DVD-ROM Disk. When I click on it to open I get a desktop floder with a heading: "CD/DVD Creator" I dont think this is correct. I would expect to see the data files, and perhaps something like VLC start up.

I get the same thing when inserting a Data DVD.

When in insert a Audio CD, I get a Audio Disk Icon on the desktop, and Sound Juicer starts. That seems correct.

When I insert a Data I get a Icon on the desktop with the CDs Name, and the DVD Recorder - File Browser comes up. That doesnt seem quite right (its not a CDR or CDRW)

I know its a lot of questions!

Thanks.
Tom
1. Have you got libdvdcss2 installed? See [http://www.ubuntuforums.org/showthread.php?t=256786](http://www.ubuntuforums.org/showthread.php?t=256786)

If you want to change the default behavior on insertion, System > Prefs > Removable Media

---

