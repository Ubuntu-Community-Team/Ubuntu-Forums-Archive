---
title: "QJoyPad 'make' error"
date: 2009-04-13
forum: Gaming &amp; Leisure
---

### Post by brenchen on 2009-04-13
Hi all,

I'm not very familiar with ubuntu but I would like to learn it. It will be very useful for me in the future I'm sure.

For now I am trying to read some USB joystick inputs into QT to do something with it. Firstly I need to detect the joystick inputs. I had a search of the web and found that QJoyPad software might be of use to me.

I tried downloading and installing it through both the way found on [http://ubuntuforums.org/showthread.php?t=147918](http://ubuntuforums.org/showthread.php?t=147918) and through the '.tgz' file following the instructed given.

Through which the .tgz way suggested, I ran the './config' then 'make'.

'.config' seemed to run fine, but when I tried the 'make' it, it returned some make error as such:
```

axis.cpp: In member function &#8216;virtual bool Axis::read(QTextStream*)&#8217;:
axis.cpp:23: error: &#8216;class QString&#8217; has no member named &#8216;lower&#8217;
axis.cpp:25: error: &#8216;split&#8217; is not a member of &#8216;QStringList&#8217;
make: *** [axis.o] Error
```
And it failed to make it.

I had a search online and it seems to be some incompatibility of QT4 (the version I'm using now) but I'm not quite sure of it.

Is there anyone that could suggest some ways to overcome this error and actually getting the QJoyPad working? Or some ways to extract/read the USB joystick inputs so I can work with through QT?

Thanks
Brendan

---

