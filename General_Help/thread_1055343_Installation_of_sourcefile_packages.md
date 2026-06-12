---
title: "Installation of sourcefile packages"
date: 2009-01-30
forum: General Help
---

### Post by tullmejs on 2009-01-30
I downloaded a program called FreeFileSync. I do not know how to build something executable from it. Contents as follows:

```
~/Desktop/Sourcecode_v1.13$ ls
algorithm.cpp               french.lng                Resources.a01
algorithm.h                 german.lng                Resources.a02
application.cpp             japanese.lng              Resources.dat
application.h               library                   Resources.rar
Changelog.txt               License.txt               synchronization.cpp
comparison.cpp              Makefile                  synchronization.h
comparison.h                Makefile_Win_Unicode.cmd  tools
dutch.lng                   mingwm10.dll              ui
FreeFileSync.h              Readme.txt                WxWizFrame.fbp
FreeFileSync - Unicode.cbp  resource.rc
```

"./Configure, make, make install" that I just learnt about doesn't seem to apply, nor are there much guidance in there. At least Readme doesn't talk about installation procedures.

:-(

---

### Post by tullmejs on 2009-01-30
found this:

[http://forums.fedoraforum.org/showthread.php?t=210480&page=2](http://forums.fedoraforum.org/showthread.php?t=210480&page=2)

> ... sometimes there is only a "Makefile"
for a "Makefile" you will need to hand edit it to match your system 

I think I'll pass :-(

I mailed the developer though.

---

### Post by tullmejs on 2009-01-30
For what it is worth, here is the makefile. One would like to think it is the first few lines that are particularly subject to edit(?) 
I am using Xubuntu Intrepid. :popcorn:

```
CPPFLAGS=-Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c
ENDFLAGS=`wx-config --libs` -lwx_gtk2_aui-2.8 -O3 -pthread

all: FreeFileSync

obj/algorithm.o: algorithm.cpp
	g++ $(CPPFLAGS) algorithm.cpp -o obj/algorithm.o

obj/comparison.o: comparison.cpp
	g++ $(CPPFLAGS) comparison.cpp -o obj/comparison.o

obj/synchronization.o: synchronization.cpp
	g++ $(CPPFLAGS) synchronization.cpp -o obj/synchronization.o

obj/application.o: application.cpp
	g++ $(CPPFLAGS) application.cpp -o obj/application.o

obj/globalFunctions.o: library/globalFunctions.cpp
	g++ $(CPPFLAGS) library/globalFunctions.cpp -o obj/globalFunctions.o

obj/guiGenerated.o: ui/guiGenerated.cpp
	g++ $(CPPFLAGS) ui/guiGenerated.cpp -o obj/guiGenerated.o

obj/mainDialog.o: ui/mainDialog.cpp
	g++ $(CPPFLAGS) ui/mainDialog.cpp -o obj/mainDialog.o

obj/syncDialog.o: ui/syncDialog.cpp
	g++ $(CPPFLAGS) ui/syncDialog.cpp -o obj/syncDialog.o

obj/customGrid.o: library/customGrid.cpp
	g++ $(CPPFLAGS) library/customGrid.cpp -o obj/customGrid.o

obj/fileHandling.o: library/fileHandling.cpp
	g++ $(CPPFLAGS) library/fileHandling.cpp -o obj/fileHandling.o

obj/multithreading.o: library/multithreading.cpp
	g++ $(CPPFLAGS) library/multithreading.cpp -o obj/multithreading.o

obj/resources.o: library/resources.cpp
	g++ $(CPPFLAGS) library/resources.cpp -o obj/resources.o

obj/smallDialogs.o: ui/smallDialogs.cpp
	g++ $(CPPFLAGS) ui/smallDialogs.cpp -o obj/smallDialogs.o

obj/misc.o: library/misc.cpp
	g++ $(CPPFLAGS) library/misc.cpp -o obj/misc.o

obj/tinyxml.o: library/tinyxml/tinyxml.cpp
	g++ $(CPPFLAGS) library/tinyxml/tinyxml.cpp -o obj/tinyxml.o

obj/tinystr.o: library/tinyxml/tinystr.cpp
	g++ $(CPPFLAGS) library/tinyxml/tinystr.cpp -o obj/tinystr.o

obj/tinyxmlerror.o: library/tinyxml/tinyxmlerror.cpp
	g++ $(CPPFLAGS) library/tinyxml/tinyxmlerror.cpp -o obj/tinyxmlerror.o

obj/tinyxmlparser.o: library/tinyxml/tinyxmlparser.cpp
	g++ $(CPPFLAGS) library/tinyxml/tinyxmlparser.cpp -o obj/tinyxmlparser.o

obj/processXml.o: library/processXml.cpp
	g++ $(CPPFLAGS) library/processXml.cpp -o obj/processXml.o
	
FreeFileSync: obj/application.o obj/algorithm.o obj/comparison.o obj/synchronization.o obj/globalFunctions.o obj/guiGenerated.o obj/mainDialog.o obj/syncDialog.o obj/customGrid.o obj/fileHandling.o obj/resources.o obj/smallDialogs.o obj/multithreading.o obj/misc.o obj/tinyxml.o obj/tinystr.o obj/tinyxmlerror.o obj/tinyxmlparser.o obj/processXml.o
	g++ $(ENDFLAGS) -o FreeFileSync obj/application.o obj/algorithm.o obj/comparison.o obj/synchronization.o obj/globalFunctions.o obj/guiGenerated.o obj/mainDialog.o obj/syncDialog.o obj/customGrid.o obj/fileHandling.o obj/resources.o obj/smallDialogs.o obj/multithreading.o obj/misc.o obj/tinyxml.o obj/tinystr.o obj/tinyxmlerror.o obj/tinyxmlparser.o obj/processXml.o


clean:
	find obj -type f -exec rm {} \;
```

---

### Post by snova on 2009-01-30
Install the **libwxgtk2.8-dev** package, and run this command:

```
make
```

If all goes well, this should be it. Copy the resulting **FreeFileSync** program wherever you like (I suggest /usr/local/bin; you'll need sudo to access that directory though).

If it doesn't work, post the output.

---

### Post by tullmejs on 2009-01-30
Sadly, no:

```
me@can:~/Desktop/Sourcecode_v1.13$ make
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c application.cpp -o obj/application.o
/bin/sh: g++: not found
make: *** [obj/application.o] Error 127
```

---

### Post by tullmejs on 2009-01-30
Found and applied this: [http://ubuntuforums.org/showthread.php?t=509997](http://ubuntuforums.org/showthread.php?t=509997)

Make again:

```
me@can:~/Desktop/Sourcecode_v1.13$ make
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c application.cpp -o obj/application.o
Assembler messages:
Fatal error: can't create obj/application.o: No such file or directory
make: *** [obj/application.o] Error 2
```

---

### Post by oldos2er on 2009-01-30
First you need to install the package build-essential. Second thing I would do would be to read Readme.txt.

---

### Post by snova on 2009-01-30
Try creating the **obj** directory.

```
mkdir obj
```

---

### Post by tullmejs on 2009-01-30
> **oldos2er said:**
> First you need to install the package build-essential

Did that, same output.

> **oldos2er said:**
> Second thing I would do would be to read Readme.txt.

> **tullmejs said:**
>  ... At least Readme doesn't talk about installation procedures.

---

### Post by tullmejs on 2009-01-30
> **snova said:**
> Try creating the **obj** directory.

```
mkdir obj
```

I did, and:

```
me@can:~/Desktop/Sourcecode_v1.13$ make
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c application.cpp -o obj/application.o
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c algorithm.cpp -o obj/algorithm.o
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c comparison.cpp -o obj/comparison.o
comparison.cpp: In function \u2018void getFileInformation(FileInfo&, const wxString&)\u2019:
comparison.cpp:122: error: cannot convert \u2018const wxChar*\u2019 to \u2018const char*\u2019 for argument \u20181\u2019 to \u2018int stat(const char*, stat*)\u2019
comparison.cpp:131: error: ambiguous overload for \u2018operator=\u2019 in \u2018output->FileInfo::lastWriteTime = buffer\u2019
/usr/include/wx-2.8/wx/string.h:676: note: candidates are: wxString& wxString::operator=(int) <near match>
/usr/include/wx-2.8/wx/string.h:956: note:                 wxString& wxString::operator=(wxChar) <near match>
/usr/include/wx-2.8/wx/string.h:970: note:                 wxString& wxString::operator=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:660: note:                 wxString& wxString::operator=(const wxString&) <near match>
make: *** [obj/comparison.o] Error 1

```

(From 127, via 2, we're now down to error 1 - must be a good thing?)

Edit: obj now holds "algorithm.o" & "application.o"

---

### Post by tullmejs on 2009-01-30
The developer ZenJu kindly responded but said little more than "*just make*".

---

### Post by snova on 2009-01-30
(Scroll down and read the last line of this post before you do any of this, you might save yourself a lot of work!)

> **tullmejs said:**
> The developer ZenJu kindly responded but said little more than "*just make*".

We've passed that, and that's pretty much what we did.

Unfortunately, these new errors are more difficult to fix.

```

comparison.cpp: In function 'void getFileInformation(FileInfo&, const wxString&)':
comparison.cpp:122: error: cannot convert 'const wxChar*' to 'const char*' for argument 1 to 'int stat(const char*, stat*)'
comparison.cpp:131: error: ambiguous overload for 'operator=' in 'output->FileInfo::lastWriteTime = buffer'
/usr/include/wx-2.8/wx/string.h:676: note: candidates are: wxString& wxString::operator=(int) <near match>
/usr/include/wx-2.8/wx/string.h:956: note:                 wxString& wxString::operator=(wxChar) <near match>
/usr/include/wx-2.8/wx/string.h:970: note:                 wxString& wxString::operator=(const wxWCharBuffer&) <near match>
/usr/include/wx-2.8/wx/string.h:660: note:                 wxString& wxString::operator=(const wxString&) <near match>

```

Much more difficult...

Well, we can try to fix the code, but I've no guarantee that it will work at all.

Open comparision.cpp in an editor, and scroll down to line 122.

```
    if (stat(filename.c_str(), &fileInfo) != 0)
```

Try replacing it with:

```
    if (stat((const char*)filename.c_str(), &fileInfo) != 0)
```

Then, down a bit to line 131:

```
    output.lastWriteTime = buffer;
```

Try:

```
    output.lastWriteTime = wxString::FromAscii(buffer);
```

I tried building it myself, and syncronization.cpp also has some problems.

Replace on line 494:

```
        if (stat(source.c_str(), &fileInfo) != 0) //read modification time from source file
```
```
        if (stat((const char*)source.c_str(), &fileInfo) != 0) //read modification time from source file
```

Line 505:

```
        if (utime(target.c_str(), &newTimes) != 0)
```
```
        if (utime((const char*)target.c_str(), &newTimes) != 0)
```

Then change the second line of Makefile:

```
ENDFLAGS=`wx-config --libs` -lwx_gtk2_aui-2.8 -O3 -pthread
```
```
ENDFLAGS=`wx-config --libs` -lwx_gtk2u_aui-2.8 -O3 -pthread
```

These replacements will fix the compilation errors (I tested them myself), but I have no guarantee whatsoever that they won't break the program's workings- it may no longer function correctly.

Have you considered finding another program for this? By the looks of it, you might be interested in rsync and its associated GUI frontends. They're even in the repos. No more compilation. :)

---

### Post by tullmejs on 2009-01-31
Listen and hear, for I will speak.

So, I heard from ZenJu again. He said I needed WxWidgets. Cool, I got it - source. I am only a couple of days into Linux, so all this is scary. But I compiled along merrily, and soon found out I really needed gtk+, or a newer, better gtk+ maybe. So I found that, the proper one actually (no it wasn't). 

Source. Cool. Now, compiling THAT, that was needed for WxWidgets that I needed for FreeFileSync that I wanted for my backup schemes, I soon realized I REALLY needed 4 packages and a couple of librarys, for gtk to compile. And then some. Then I had picked wrong gtk stuff anyway, but I found more, better, this time somewhat easier through apt-get.

Now it actually runs, possibly smooth. We'll see.

Thanks all!

---

### Post by tullmejs on 2009-03-13
Hello, I am back to Error 1.

I made a new install, this time Ubuntu instead of Xubuntu. Now I try to get FreeFileSync installed too.

I got build-essential, g++, gtk+ and wxwidgets, but I still get Error 1 on MAKEing...

I have asked the developer again, but I think I also lack general understanding of Ubuntu and Linux. I'd like to have some idea about where to look, how to begin to analyse the difficulties.

Since I actually got it up and running last time, I think I'll pass on snova:s suggested fix, but I certainly appreciate the effort!

---

### Post by tullmejs on 2009-03-13
Edit: urged by developer, I tried a new version, output updated accordingly.

Might help:

```
root@S:/home/laban/ffs# make
if [ ! - d obj ]; then mkdir obj; fi
[: 1: d: unexpected operator
g++ -Wall -pipe -DNDEBUG `wx-config --cppflags` -DFFS_LINUX -DTIXML_USE_STL -O3 -pthread -c application.cpp -o obj/application.o
In file included from application.cpp:8:
application.h:84: error: ISO C++ forbids declaration of &#8216;auto_ptr&#8217; with no type
application.h:84: error: invalid use of &#8216;::&#8217;
application.h:84: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
application.h:86: error: ISO C++ forbids declaration of &#8216;auto_ptr&#8217; with no type
application.h:86: error: invalid use of &#8216;::&#8217;
application.h:86: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
In file included from application.cpp:9:
ui/mainDialog.h:219: error: ISO C++ forbids declaration of &#8216;auto_ptr&#8217; with no type
ui/mainDialog.h:219: error: invalid use of &#8216;::&#8217;
ui/mainDialog.h:219: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
application.cpp: In member function &#8216;void Application::runBatchMode(const wxString&, xmlAccess::XmlGlobalSettings&)&#8217;:
application.cpp:272: error: &#8216;auto_ptr&#8217; is not a member of &#8216;std&#8217;
application.cpp:272: error: expected primary-expression before &#8216;>&#8217; token
application.cpp:272: error: &#8216;statusHandler&#8217; was not declared in this scope
application.cpp:274: error: &#8216;auto_ptr&#8217; is not a member of &#8216;std&#8217;
application.cpp:274: error: expected primary-expression before &#8216;>&#8217; token
application.cpp:276: error: &#8216;auto_ptr&#8217; is not a member of &#8216;std&#8217;
application.cpp:276: error: expected primary-expression before &#8216;>&#8217; token
application.cpp: At global scope:
application.cpp:399: error: ISO C++ forbids declaration of &#8216;auto_ptr&#8217; with no type
application.cpp:399: error: invalid use of &#8216;::&#8217;
application.cpp:399: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
application.cpp:400: error: ISO C++ forbids declaration of &#8216;auto_ptr&#8217; with no type
application.cpp:400: error: invalid use of &#8216;::&#8217;
application.cpp:400: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
application.cpp: In constructor &#8216;FfsTrayIcon::FfsTrayIcon(StatusHandler*)&#8217;:
application.cpp:329: error: &#8216;running&#8217; was not declared in this scope
application.cpp:330: error: &#8216;paused&#8217; was not declared in this scope
application.cpp: In member function &#8216;void FfsTrayIcon::onContextMenuSelection(wxCommandEvent&)&#8217;:
application.cpp:366: error: &#8216;paused&#8217; was not declared in this scope
application.cpp:368: error: &#8216;running&#8217; was not declared in this scope
application.cpp:373: error: &#8216;running&#8217; was not declared in this scope
application.cpp: In constructor &#8216;BatchStatusHandlerSilent::BatchStatusHandlerSilent(xmlAccess::OnError, int&)&#8217;:
application.cpp:408: error: class &#8216;BatchStatusHandlerSilent&#8217; does not have any field named &#8216;trayIcon&#8217;
application.cpp:409: error: class &#8216;BatchStatusHandlerSilent&#8217; does not have any field named &#8216;m_log&#8217;
application.cpp:412: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In destructor &#8216;virtual BatchStatusHandlerSilent::~BatchStatusHandlerSilent()&#8217;:
application.cpp:428: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp:433: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp:436: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual void BatchStatusHandlerSilent::updateStatusText(const Zstring&)&#8217;:
application.cpp:444: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual ErrorHandler::Response BatchStatusHandlerSilent::reportError(const Zstring&)&#8217;:
application.cpp:474: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp:490: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual void BatchStatusHandlerSilent::reportFatalError(const Zstring&)&#8217;:
application.cpp:527: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual void BatchStatusHandlerSilent::reportWarning(const Zstring&, bool&)&#8217;:
application.cpp:550: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp:562: error: &#8216;m_log&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual void BatchStatusHandlerSilent::forceUiRefresh()&#8217;:
application.cpp:576: error: &#8216;trayIcon&#8217; was not declared in this scope
application.cpp: In member function &#8216;virtual void BatchStatusHandlerSilent::exitAndSetStatus(const wxString&, BatchStatusHandler::ExitCode)&#8217;:
application.cpp:593: error: &#8216;m_log&#8217; was not declared in this scope

make: *** [obj/application.o] Error 1
root@S:/home/laban/ffs# 
```

---

