---
title: "Extracting data from recently-used.xbel?"
date: 2020-09-13
forum: Desktop Environments
---

### Post by erza-k-rot on 2020-09-13
Hi everyone!


This is my first world problem: I'm so glad I moved to Xubuntu for the past few weeks - I have optimized everything and learned a lot in the process. But there's something I just can't get used to: in Windows, right-clicking on the task bar Explorer icon will give you a list of the last folders you were active in. This is so useful! Helps not have 15 tabs open while you're working on a bunch of stuff.

So I spent the day looking for a way to get these folders up and ready to open. And it's no easy task for a newbie like myself. No dock app or file manager offers this option which I find hard to believe!


Two things I discovered: what I'm looking for is EXACTLY what is displayed when you go there in Xubuntu: desktop right-click > desktop settings > folder > other... > RECENTLY USED...! That's the one. I would love to be able to display this list of folders very quickly.

The second thing I discovered was the file /home/USER/.local/share/recently-used.xbel which I assume the aformentioned "recently used" folder gets its data from.


If someone could help me find a way to do this, I would be eternally grateful. Thanks for reading, and stay safe out there.

---

### Post by geofftf on 2020-09-14
Google found an answer to this. Open a terminal and type:

```
sudo apt install gvfs-bin
```

Type your password when prompted. Type:

```
gvfs-open recent:///
```

That worked for me, but I got "This tool has been deprecated, use 'gio open' instead. See 'gio help open' for more info." This message has been reported as Ubuntu Bug #1721948.

You should be able to set up a shortcut key to launch this application:

[HTML]https://www.unixmen.com/how-to-add-shortcut-keys-in-xfce/[/HTML]

---

### Post by erza-k-rot on 2020-09-14
geoff, thank you immensely for your reply. It will definitely help down the line. Now, I discovered recent:/// yesterday, but what I'm really looking for is recent folders! It only displays files. Of course there is the "location" column, but the long paths, the amount of different files and the right-clicking 'open location' don't really do the trick.

The fact that what I'm looking for is available in [desktop settings>folder>other] makes it all seem so *possible*! Any more ideas? Definitely on the right path with the shortcut!

Thanks again for your kind interest.

---

### Post by ajgreeny on 2020-09-14
You can open those ~/.local/share/recently-used.xbel files, of which I have many, using a text-editor, and you could then get the information you needed, though perhaps not quite in the way you're wanting.

I am not good enough at bash to give you a command to extract the folders and files shown but there will be ways, I'm pretty sure of that.
You can start with a simple grep command ```
grep /***yourusername***/ .local/share/recently-used.xbel
``` (showing your real username of course) which will then show all the lines with pathways to files and folders in your home that you have opened.
If you've opened files in the root system you can also look for those by replacing the /***yourusername***/ with ***/etc/*** or ***/lib/***, etc etc.

---

### Post by geofftf on 2020-09-14
awk would be a better tool than grep. With awk it is possible to split the matched lines into fields, and extract just the path names. It is then possible to sort the resulting lines and remove duplicates using sort and uniq, and concatenate the resulting lines separated by spaces. The resulting string can be added on the end of "thunar ". If you run that as terminal command Thunar should open with all the matched directories as tabs. I am not a terminal command expert (especially late at night), so you would have to fill in the details yourself. You will find some clues here:

[HTML]https://stackoverflow.com/questions/15580144/how-to-concatenate-multiple-lines-of-output-to-one-line[/HTML]

Better still, you could write a little Python program to construct the thunar command, and Python can launch the command too. You could also set up a keyboard shortcut to launch the Python program.

---

### Post by Holger_Gehrke on 2020-09-14
With the use of hxselect from the package html-xml-utils (don't know whether or not that's installed by default) you can extract the href-attribute of the bookmark-element in the recently-used.xbel file. With a bit of 'sed' and 'sort -u' this
```

hxselect -c -s '\n' 'bookmark::attr(href)'<$HOME/.local/share/recently-used.xbel|sed -n 's/\(file:\/\/.*\/\).*/\1/p'|sort -u

```
prints out just the directories for all the files as 'file://'-urls. If you execute that line in the xfce4-terminal you can open the directories in thunar by right-clicking on them and selecting an option from the context-menu.

Holger

---

### Post by geofftf on 2020-09-15
That is awesome. I found to sed bit hard to follow. It converts file paths into the corresponding directory paths. Here is another sed command that achieves the same result:

[HTML]https://unix.stackexchange.com/questions/482477/regex-delete-all-characters-after-the-last-occurrence-of[/HTML]

With that, the command becomes:

```
hxselect -c -s '\n' 'bookmark::attr(href)'<$HOME/.local/share/recently-used.xbel | sed 's![^/]*$!!' | sort -u
```

I have tested that and it works. It should be possible to set up a keyboard shortcut or .desktop file (to create a menu entry) that kicks the command off.

---

### Post by erza-k-rot on 2020-09-15
You guys, this is amazing -- thank you so much! I didn't think we  would get this far so quick!

Now, I'm left with one last problem: since  I'm french, and also using a cloud service, the results look like these:  "pr%C3%A9l%C3%A8vements" (because of those éè etc), and can get pretty lengthy too! So in the  end I spend as much time reading the results than getting to the  folder...!
Would anyone know of a way to actually open up a folder  containing shortcuts? Geoff, it seems like you were definitely close  when you said

> **geofftf said:**
> The resulting string can be added on the end of "thunar ". If you run that as terminal command Thunar should open with all the matched directories as tabs

but I don't quite understand what to do there, and also if opening all of them can be avoided, that would be great too.

Again, thanks everyone for your help, and when we find a solution I'll definitely be sending it to a good number of people I've found looking for this.

---

### Post by geofftf on 2020-09-15
I did not read the man page for Thunar carefully enough. I said it was late at night. Each file path parameter opens a new window. Here is the command, for what it is worth:

```
hxselect -c -s '\n' 'bookmark::attr(href)'<$HOME/.local/share/recently-used.xbel | sed 's![^/]*$!!' | sort -u | tr '\n' ' ' | awk '{print "thunar ", $0}' | bash
```

An interesting exercise, but useless. I think the solution that we already have is the best one. Sorting out the character mapping problem would appear to be the way forward.

---

### Post by geofftf on 2020-09-15
I may have a solution for you. Xubuntu 20.04 ships with the Dolphin file manager in addition to Thunar. Dolphin offers the options of modified today and modified yesterday. If that is not enough, there are plenty of other file managers that you could install.

---

### Post by ajgreeny on 2020-09-15
Dolphin is not installed in Xubuntu by default; to do so will need 149 extra packages to be installed on my default Xubuntu-20.04 system, mainly because dolphon requires a lot of the KDE/qt libs etc.
This in itself is not necessarily a problem, but geofftf made it sound as if dolphin was already installed in Xubuntu; it is not, so be warned.

---

### Post by Holger_Gehrke on 2020-09-15
A bit shorter without either awk or an additional shell and with a command substitution:
```

thunar $(hxselect -c -s '\n' 'bookmark::attr(href)'<$HOME/.local/share/recently-used.xbel | sed 's![^/]*$!!' | sort -u | tr '\n' ' ')

```
Both these solutions have one fatal flaw: if any of the directories does not exist because it was removed after working on files in it or because it's on external media which are not currently on line, thunar shows an error and does not open any windows. Since that's quite a normal situation - at least for me, I tend to create temporary working directories and remove them again once I'm done - this one liner is basically useless as it is. To filter out the non-existing paths we'd first need to convert the 'file://'-urls to normal paths; then we could just loop over the lines and remove any that don't exist.

But while there are [several script snippets for decoding urls  on stackexchange]("https://unix.stackexchange.com/questions/159253/decoding-url-encoding-percent-encoding"), those are not enough in this case. If you have any special characters in your directory names - for example ampersand or apostrophe - these will have been translated to xml-entities - like &amp; and &apos;. The simplest way to translate these back into characters is to add some more substitutions to the sed script.

In my final version I've used urlencode from the package gridsite-clients for url decoding and zenity (package zenity) to produce a graphical selection:
```

thunar "$(for i in $(hxselect -c -s '\n' 'bookmark::attr(href)'<$HOME/.local/share/recently-used.xbel | sed 's![^/]*$!!;s/&apos;/'\''/g;s/&amp;/&/g' | sort -u); do a=$(urlencode -d "$i");a=${a##file://}; if [ -d "$a" ] ; then echo $a; fi; done|zenity --width 1000 --text "Recently used directories" --list --radiolist --column="" --column="Directory Name")"

```

Not exactly beautiful, but it demonstrates the software-tools philosophy: many small programs - each with one well-defined purpose - used together to do a bigger job.

Holger

---

### Post by geofftf on 2020-09-15
I am very impressed Holger. That is well beyond my beginner's skills at Bash scripting. I get a warning when I run your script:

```
(zenity:3050): GLib-WARNING **: 20:08:29.209: ../../../glib/giounix.c:410Error while getting flags for FD: Bad file descriptor (9)
```

Nonetheless, I was able to select a file click it and open Thunar, but the graphical window then disappeared. It would be helpful it remained in place.

I do not understand why the OP is getting problems displaying French characters in the terminal but (I assume) not elsewhere.

I do not know how often the .xbel file is weeded, or whether that is configurable. It may be that we need to only select files that were accessed within x days of the current date. That is getting a bit beyond a one liner.

As far as Dolphin is concerned, I have it on my Xubuntu 20.04 system, but I did not install it. The only KDE application that I have installed is ShowFoto (DigiKam with the photo editing functions, but without the database functions). ShowFoto took a long time to install and pulled in about 600 MB of dependencies (if I remember correctly). Perhaps it pulled in Dolphin, which does seem out of place. ShowFoto loads very quickly and does not take up much RAM.

I have got doubts about whether Dolphin would be useful to the OP. It does have recently accessed buttons on the front page, but they pull up files as well as directories.

---

### Post by Holger_Gehrke on 2020-09-15
That warning could be the result of zenity actually expecting a file and not the output from a pipe ... It's trying to get some flags from the file descriptor and it seems a pipe doesn't have the flags it's looking for.

Keeping the list window around is not possible because of the way zenity works. Once you click 'OK' the form is removed and the selection is sent to standard output.

And it's not only the OP having problems with French characters in the .xbel file. My German umlauts encoded in UTF-8 are also shown as %XX%YY. This is because URLs were originally defined as only containing ASCII characters. So any national special characters are rewritten in the percentage-sign notation.

AFAIK the .xbel file(s) are not weeded at all. I have three files in ~/.local/share, two of them with additional, random looking suffixes at the end. The oldest one has a date about one year after installation and the second is about one and a half years newer than the oldest.I think it waits until either an age or a size limit is reached and starts a new file. There are three time stamps stored for every bookmark in the .xbel-file. One could get these the same way as the href-attribute, probably in the same call to hxselect and with an -s option to set a separator between the URL and the timestamps.

IMO the right way to use this would be to put it in a script, make a .desktop file for it and have that in a starter on a panel (that would also hide the warning; it would probably go into ~/xsession-errors). Or one could define a shell-function or an alias for it and have it in ~/.bashrc (and add a redirection for standard error to /dev/null to the call to zenity to hide the warnings).

Strangely I have quite a few KDE / QT applications in my system (DigiKam, Clementine, Sigil, ...) and Dolphin has not been pulled in. Might be a difference between 18.04 and 20.04.

Holger

---

### Post by erza-k-rot on 2020-09-16
> **Holger_Gehrke said:**
> Not exactly beautiful

Are you kidding :P You guys, to me this is nothing short of magical, I'm sincerely admirative of your skill and dedication. Thanks a million to you guys for powering through this dark path with your wizardy shenanigans.

Geoff, before posting this thread I was nearly ready to switch to KDE for that feature, so I'm stoked about what you're saying. I suppose you can sort the recent folder by type to get the folders on top? (Also after 19.04 upgrade I re-installed 18.04 for its shorter booting time, but this would make me switch back - although do you find the new versions get heavier too?)

One last trick I was trying was [copying the current path]("https://forums.solydxk.com/viewtopic.php?t=5472") on Thunar, hoping to access the now famous 'desktop settings>folder>other', but my custom action just doesn't appear when I'm in there. I can't help but wonder, the "recipe" to this folder surely is encoded *somewhere*?

---

### Post by geofftf on 2020-09-16
Yes, Dolphin allows you to sort by type so that the folders appear on top within a directory. That is usual behaviour. Thunar provides a check box for that which is set by default.  Here is the Dolphin handbook:

[https://docs.kde.org/trunk5/en/applications/dolphin/dolphin.pdf](https://docs.kde.org/trunk5/en/applications/dolphin/dolphin.pdf)

As you will see Dolphin has recently saved options of today, yesterday, this month and last month on the front page.

I am running Xubuntu 20.04 on an HP 4300 SFF that I bought from eBay for £49 including postage. It has third generation i3-3220 and 4 GB of DDR3 RAM. I have replaced the 500 GB hard disk with a Kingston A400 120 GB SSD.

geoff@HP:~$ systemd-analyze
Startup finished in 1.409s (kernel) + 6.633s (userspace) = 8.043s 
graphical.target reached after 6.616s in userspace

That is quick enough for me. A used i5-3470S costs about £20 and another 4 GB about £11. Not a lot of money, but there is no point in upgrading right now.

Lubuntu 20.04 takes about 50 MB less than Xubutu 20.04 after a fresh boot. The Lubuntu team is trying to keep the memory usage down by only using Qt5, but LibreOffice Draw is rubbish with Qt5. I am also using Google Chrome. Does that use Qt5? I doubt it.

---

### Post by geofftf on 2020-09-19
I have written a Python program to do this as a beginner's exercise:

```
import os
import csv
from datetime import date
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 100

# Extract the directory path names and modification dates from the recently-used.xbel file
path = os.environ['HOME'] + '/.local/share/recently-used.xbel'
file = open(path)
csv_f = csv.reader(file, delimiter = '"')
PathDate = []
for row in csv_f:
    if row[0] == '  <bookmark href=' and row[1][0:8] == 'file:///':
        FilePath = row[1][7:]
        ModifiedDate = row[5][:10]
        LastSlash = FilePath.rindex('/')
        DirectoryPath = FilePath[:LastSlash]
        PathDate.append(DirectoryPath + ModifiedDate)

# Sort into descending order of path and then modification date.
PathDate.sort(reverse=True)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDate:
    Path = row[:-10]
    Year = int(row[-10:-6])
    Month = int(row[-5:-3])
    Day = int(row[-2:])
    Date = date(Year, Month, Day)
    DeltaDays = (date.today() - Date).days
    if Path != PrevPath and DeltaDays <= MaxDays:
        Pruned.append(Path)
        PrevPath = Path

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]]])

# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Listbox and attach it to the left side of the root window.
listbox = Listbox(root, height = 20, width = 50)
listbox.pack(side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event to the listbox.
listbox.bind('<ButtonRelease-1>', on_click_listbox)

# Insert the path names with special characters into the listbox.
for Path in Pruned:
    listbox.insert(END, urllib.parse.unquote(Path))

root.mainloop()
```

You can run it by typing python3 followed by the file name in  a terminal. You can set up a keyboard short cut or a desktop file as discussed before. I believe this program avoids the limitations of the terminal commands discussed previously. Special characters are displayed, we have a persistent window and we can click on as many directory names as we choose. I have set a parameter to ensure that only directories with files that were modified within the last 100 days are displayed, but that number can easily be changed in the code. It would not be difficult to add a widget to the GUI to perform that function.

---

### Post by Holger_Gehrke on 2020-09-19
I rarely use Python, but I know that XML handling is part of the standard library (take a look at xml.dom.minidom). And since the .xbel file is XML using those functions would probably make the code shorter, more readable and more robust.

Holger

---

### Post by geofftf on 2020-09-19
I expect that you are right Holger. I do not understand xml, but perhaps I should educate myself. Provided the underlying file format does not change, my code should be OK. I could make it shorter by eliminating the single use variables, but that would not help with readability. The Python documentation page for xml.dom.minidom is:

[https://docs.python.org/3/library/xml.dom.minidom.html](https://docs.python.org/3/library/xml.dom.minidom.html)

That page recommends xml.etree.ElementTree for beginners like me:

[https://docs.python.org/3/library/xml.etree.elementtree.html#module-xml.etree.ElementTree](https://docs.python.org/3/library/xml.etree.elementtree.html#module-xml.etree.ElementTree)

That is as clear as mud to me. Here is a more readable tutorial:

[https://eli.thegreenplace.net/2012/03/15/processing-xml-in-python-with-elementtree/](https://eli.thegreenplace.net/2012/03/15/processing-xml-in-python-with-elementtree/)

Using xml.etree.ElementTree might make the code more robust to changes. Have you tried running my script? Do the umlauts show up clearly?

---

### Post by Holger_Gehrke on 2020-09-19
Yes, both Umlauts and characters transcribed into entities (&amp; and &apos; happen to be in directory-names I have in my list of recently used files) work as they should.

What you've forgotten about is the case of a directory having been deleted after being put in recently-used.xbel. I've tried my hand at using minidom and fixing that problem and keeping path and date separate by having dictionaries as elements of the list
```

import os
from xml.dom import minidom
from datetime import date
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 100

# Extract the directory path names and modification dates from the recently-used.xbel file

mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDate = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    if os.path.exists(urllib.parse.unquote(filepath)[7:]):
        PathDate.append({'path':os.path.dirname(filepath),'date':moddate})

def keyfunc(item):
    return item['path']+item['date']

# Sort into descending order of path and then modification date.
PathDate.sort(reverse=True,key=keyfunc)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDate:
    Path = row['path']
    Year = int(row['date'][0:4])
    Month = int(row['date'][5:7])
    Day = int(row['date'][8:10])
    Date = date(Year, Month, Day)
    DeltaDays = (date.today() - Date).days
    if Path != PrevPath and DeltaDays <= MaxDays:
        Pruned.append(Path)
        PrevPath = Path

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]]])

# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Listbox and attach it to the left side of the root window.
listbox = Listbox(root, height = 20, width = 100)
listbox.pack(side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event to the listbox.
listbox.bind('<ButtonRelease-1>', on_click_listbox)

# Insert the path names with special characters into the listbox.
for Path in Pruned:
    listbox.insert(END, urllib.parse.unquote(Path))

root.mainloop()


```

Holger

---

### Post by geofftf on 2020-09-19
You have made some good improvements. Keeping the path and date separate by using a key function for the sort is good style. What I do not like is your use of a dictionaries. A more appropriate language construct is the named tuple. I have modified the code to use a named tuple in place of the two dictionaries. You have widened the window and I have made it deeper.

```
import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 100

pathdate = namedtuple('pathdate', ['path', 'date'])

# Extract the directory path names and modification dates from the recently-used.xbel file
mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDate = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    if os.path.exists(urllib.parse.unquote(filepath)[7:]):
        PathDate.append(pathdate(os.path.dirname(filepath), moddate))

def keyfunc(item):
    return item.path + item.date

# Sort into descending order of path and then modification date.
PathDate.sort(reverse=True,key=keyfunc)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDate:
    Path = row.path
    Year = int(row.date[0:4])
    Month = int(row.date[5:7])
    Day = int(row.date[8:10])
    Date = date(Year, Month, Day)
    DeltaDays = (date.today() - Date).days
    if Path != PrevPath and DeltaDays <= MaxDays:
        Pruned.append(Path)
        PrevPath = Path

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]]])

# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Listbox and attach it to the left side of the root window.
listbox = Listbox(root, height = 30, width = 100)
listbox.pack(side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)

# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event to the listbox.
listbox.bind('<ButtonRelease-1>', on_click_listbox)

# Insert the path names with special characters into the listbox.
for Path in Pruned:
    listbox.insert(END, urllib.parse.unquote(Path))

root.mainloop()

```

I have spotted an issue. I visited some icon directories in /usr/share, but did not change anything. They are in the .xbel file with a modified date. Very strange.

---

### Post by Holger_Gehrke on 2020-09-19
As I said, I use python rarely. Hadn't even heard of named tuples ... but you're right, it looks cleaner. Actually using a sort function was born out of my desire not to mix separate pieces of data together because I don't like unscrambling eggs, so the dictionary came first and then the sort function was a matter of necessity. 

I'd think the modification date is the modification date of the entry, not the file. So since you opened the directory, a new entry was created with a modification date of today ...

Five more small changes:

[LIST]
[*]I like array variables to have names in plural form, since they hold many things. So I changed PathDate to PathDates. Just a stylistic thing. Also reduces the probability of mixing up pathdate the named tuple and PathDates the array. 
[*]Import of the parser from dateutil to get rid of the slicing and dicing of the timestamp and simply convert that into a datetime (and that into a date). 
[*]Find the longest path and use that to set the listbox width. 
[*]Keyboard control: Set the focus to the listbox, bind the Return key to select the current element and ^q to quit. 
[*]Set the listbox to expand if the window is resized. 
[/LIST]

```

import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 100

# find max path-length for width of listbox
MaxPathLength = 0

# named tuple for storage of the entries
pathdate = namedtuple('pathdate',['path','date'])

# Extract the directory path names and modification dates from the recently-used.xbel file

mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDates = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    fp=urllib.parse.unquote(filepath)[7:]
    if os.path.exists(fp):
        if len(fp) > MaxPathLength:
            MaxPathLength = len(fp)
        PathDates.append(pathdate(os.path.dirname(filepath),moddate))

# sort needs a function to give it a key if the list contains complex elements
def keyfunc(item):
    return item.path + item.date

# Sort into descending order of path and then modification date.
PathDates.sort(reverse=True,key=keyfunc)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDates:
    Path = row.path
    # using parser from dateutils to get a datetime from the timestamp string
    # and then turning that into a date
    DeltaDays = (date.today() - parser.parse(row.date).date()).days
    if Path != PrevPath and DeltaDays <= MaxDays:
        Pruned.append(Path)
        PrevPath = Path

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]]])

# Event Handler for ^q=quit
def finish(event):
    quit()

# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Listbox and attach it to the left side of the root window
# MaxPathLength as width is too much since it assumes a fixed-width font, multiplying by .7 seems to give a good result
listbox = Listbox(root, height = 30, width = int(MaxPathLength * 0.7))

# Insert the path names with special characters into the listbox.
for Path in Pruned:
    listbox.insert(END, urllib.parse.unquote(Path))

listbox.pack(expand=1, side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and a Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
listbox.bind('<Return>',on_click_listbox)
# Bind Ctrl-q to finish
listbox.bind('<Control-q>',finish)
listbox.set_focus()

root.mainloop()

```

One nitpick remaining, making the window narrower makes the scrollbar vanish. Probably something to do with the pack layout-manager.

Holger

---

### Post by geofftf on 2020-09-20
Yes, that is much improved. One little problem though. Listbox does not have a set_focus attribute. I have changed that to focus_set, which does work.

```
import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 100

# find max path-length for width of listbox
MaxPathLength = 0

# named tuple for storage of the entries
pathdate = namedtuple('pathdate',['path','date'])

# Extract the directory path names and modification dates from the recently-used.xbel file
mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDates = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    fp=urllib.parse.unquote(filepath)[7:]
    if os.path.exists(fp):
        if len(fp) > MaxPathLength:
            MaxPathLength = len(fp)
        PathDates.append(pathdate(os.path.dirname(filepath),moddate))

# sort needs a function to give it a key if the list contains complex elements
def keyfunc(item):
    return item.path + item.date

# Sort into descending order of path and then modification date.
PathDates.sort(reverse=True,key=keyfunc)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDates:
    Path = row.path
    # using parser from dateutils to get a datetime from the timestamp string
    # and then turning that into a date
    DeltaDays = (date.today() - parser.parse(row.date).date()).days
    if Path != PrevPath and DeltaDays <= MaxDays:
        Pruned.append(Path)
        PrevPath = Path

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]]])

# Event Handler for ^q=quit
def finish(event):
    quit()

# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Listbox and attach it to the left side of the root window
# MaxPathLength as width is too much since it assumes a fixed-width font, multiplying by .7 seems to give a good result
listbox = Listbox(root, height = 30, width = int(MaxPathLength * 0.7))
# Insert the path names with special characters into the listbox.
for Path in Pruned:
    listbox.insert(END, urllib.parse.unquote(Path))
listbox.pack(expand=1, side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and a Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
listbox.bind('<Return>',on_click_listbox)
# Bind Ctrl-q to finish
listbox.bind('<Control-q>',finish)
listbox.focus_set()

root.mainloop()

```
I do not write much Python either. I wrote a few little programs a few years ago. I have to keep looking up the syntax. Named tuples are pretty fundamental - the equivalent of a record in Pascal or a struct in C.  It did not take me long to look for the Python equivalent. I can remember the syntax for Fortran IV, with anything else I am struggling.

---

### Post by geofftf on 2020-09-20
The other refinement that I had considered was to make Pruned store both the path and date rather than just the date. We could then put a text box in the window to change MaxDays and re-display the paths with that date as a filter.

---

### Post by geofftf on 2020-09-20
I have modified the program to include a text box for setting the maximum number of days before the current day for which accesses are to be displayed.

```
import osfrom xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 90

# find max path-length for width of listbox
MaxPathLength = 0

# Named tuple for storage of entries.
pathdate = namedtuple('pathdate',['path','date'])

# Extract the directory path names and modification dates from the recently-used.xbel file
mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDates = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    fp=urllib.parse.unquote(filepath)[7:]
    if os.path.exists(fp):
        if len(fp) > MaxPathLength:
            MaxPathLength = len(fp)
        PathDates.append(pathdate(os.path.dirname(filepath),moddate))

# sort needs a function to give it a key if the list contains complex elements
def keyfunc(item):
    return item.path + item.date

# Sort into descending order of path and then modification date.
PathDates.sort(reverse=True,key=keyfunc)

# Remove old or duplicate rows.
Pruned = []
PrevPath = ''
for row in PathDates:
    Path = row.path
    if Path != PrevPath:
        # Use the parser from dateutils to get a datetime from the timestamp string
        # and then turn that into a date.
        Date = parser.parse(row.date).date()
        Pruned.append(pathdate(Path,Date))
        PrevPath = Path

# Event handler for <CR> in the entry field.
def on_return_entry(event):
    global MaxDays
    try:
        MaxDays = int(event.widget.get())
    except:
        Maxdays = 90
    fill_listbox()

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar for the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]].path])

# Event Handler for ^q=quit
def finish(event):
    quit()
    
# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Frame at the bottom of the root window.
frame = Frame(root)
frame.pack(side=BOTTOM)

# Create a text label on the left of the Frame.
label = Label(frame, text='Maximum days accessed before today')
label.pack(side=LEFT)

# Create an entry field on the right of the Frame.
entry = Entry(frame, width=5)
entry.insert(0, '90')
entry.bind('<Return>', on_return_entry)
entry.pack(side=RIGHT)

# Create a Listbox and attach it to the left side of the root window
# MaxPathLength as width is too much since it assumes a fixed-width font,
# multiplying by .7 seems to give a good result.
listbox = Listbox(root, height = 30, width = int(MaxPathLength * 0.7))
listbox.pack(expand=1, side = LEFT, fill = BOTH)

def fill_listbox():
    # If the date is within range, fill the list box with the path names with special characters.
    listbox.delete(0, END)
    for row in Pruned:
        DeltaDays = (date.today() - row.date).days
        if DeltaDays <= MaxDays:
            listbox.insert(END, urllib.parse.unquote(row.path))

fill_listbox()

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and a Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
listbox.bind('<Return>',on_click_listbox)
# Bind Ctrl-q to finish
listbox.bind('<Control-q>',finish)
listbox.focus_set()

root.mainloop()

```

Everything seems to work, but I am not convinced that the "modified" dates in the .xbel file make a lot of sense.

---

### Post by erza-k-rot on 2020-09-20
Geoff and Holger, this is stunning. I can't believe you guys managed to program the *exact* thing!

I tried to figure three things out and managed one: to sort by date, I swapped 'date' and 'path' in this line, resulting in: return item.date + item.path. Correct? But when I do this, the duplicate rows all show up again, I don't know why.

Now, for the two other things I couldn't solve: how would you display only the folder names instead of the full path? And how would you set a limit to the number of items in the list? (it seems this intention is un-pythonesque from what I gather)

---

### Post by geofftf on 2020-09-21
The purpose of the sort in the program is to remove duplicate path names. It sorts in descending order of path, and then date. Each group of duplicate paths is then together in the list, in descending order of date. For each group of duplicate paths, the program then selects the first entry for each path from the list, which will be the one with the most recent date. If you reverse the path and date this algorithm will not work.

I will modify the program.

Geoff.

---

### Post by geofftf on 2020-09-21
I have modified the program to display the paths is descending order of the last access date.

```
import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 90

# find max path-length for width of listbox
MaxPathLength = 0

# Named tuple for storage of entries.
pathdate = namedtuple('pathdate',['path','date'])

# Extract the directory path names and modification dates from the recently-used.xbel file

mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
bookmarkNodeList=mydom.getElementsByTagName('bookmark')
PathDates = []
for bookmarkNode in bookmarkNodeList:
    filepath=bookmarkNode.getAttribute('href')
    moddate=bookmarkNode.getAttribute('modified')
    fp=urllib.parse.unquote(filepath)[7:]
    if os.path.exists(fp):
        if len(fp) > MaxPathLength:
            MaxPathLength = len(fp)
        PathDates.append(pathdate(os.path.dirname(filepath),moddate))

# Sort PathDates into descending order of path and then modification date.

# Sort needs a function to give it a key because the list contains complex elements.
def pd_keyfunc(item):
    return item.path + item.date

PathDates.sort(reverse=True,key=pd_keyfunc)

# Each group of duplicate paths is now together in the list, in descending order of date.
# For each group of duplicate paths, select the first entry for each path from the list,
# which will be the one with the most recent date.
Pruned = []
PrevPath = ''
for row in PathDates:
    Path = row.path
    if Path != PrevPath:
        # Use the parser from dateutils to get a datetime from the timestamp string,
        # and then turn that into a date.
        Date = parser.parse(row.date).date()
        Pruned.append(pathdate(Path,Date))
        PrevPath = Path

# Sort Pruned into descending order of date.

# Sort needs a function to give it a key because the list contains complex elements.
def p_keyfunc(item):
    return item.date

Pruned.sort(reverse=True,key=p_keyfunc)

# Event handler for <CR> in the entry field.
def on_return_entry(event):
    global MaxDays
    try:
        print(int(event.widget.get()))
        MaxDays = int(event.widget.get())
    except:
        entry.delete(0, END)
        entry.insert(0, 'Error')
    fill_listbox()

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar with the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]].path])

# Event Handler for ^q=quit
def finish(event):
    quit()
    
# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")

# Create a Frame at the bottom of the root window.
frame = Frame(root)
frame.pack(side=BOTTOM)

# Create a text label on the left of the Frame.
label = Label(frame, text='Maximum days folder accessed before today')
label.pack(side=LEFT)

# Create an entry field on the right of the Frame.
entry = Entry(frame, width=5)
entry.insert(0, str(MaxDays))
entry.bind('<Return>', on_return_entry)
entry.pack(side=RIGHT)

# Create a Listbox and attach it to the left side of the root window.
# Using MaxPathLength as the width is too much because it assumes a fixed-width font.
# Multiplying by .7 seems to give a good result.
listbox = Listbox(root, height = 30, width = int(MaxPathLength * 0.7))
listbox.pack(expand=1, side = LEFT, fill = BOTH)

# Fill the listbox with the path names with special characters, when the date is within range. 
def fill_listbox():
    listbox.delete(0, END)
    for row in Pruned:
        listbox.insert(END, urllib.parse.unquote(row.path[7:]))
        if (date.today() - row.date).days > MaxDays:
            break

fill_listbox()

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = BOTH)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and a Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
listbox.bind('<Return>',on_click_listbox)
# Bind Ctrl-q to finish
listbox.bind('<Control-q>',finish)
listbox.focus_set()

root.mainloop()
```

Xubuntu has directories with the same name in many places. Some users will want the full path name. I am not sure how to tackle that one. Try the modified program and see what you think.

Do we need to text box at the bottom of the window now that we are sorting into descending order of access date? If the user does not want to look at files that were not accessed recently, he does not have to scroll down that far. Adding the text box  and its label complicates the program and makes it a little messy, because of the order in which the widgets have to be packed. Would it be helpful to show the access dates at the beginning of each line?

---

### Post by erza-k-rot on 2020-09-21
This is really great stuff!

This display is perfect for me and definitely makes things clearer: I can find a folder  exactly where I expect it, because it shows in which order I worked. I  believe this is also the reason why in Windows, the same kind of menu  would only display folder names - even with the same name, the order  would tell them apart easily; whereas since the end folders are  not in a column, it takes me some time finding the end of each line to  figure them out. Then again, maybe I'm not as used to heavier visual  information as more experienced xubuntu users!

For the text box: to me, this program is more of a day-by-day need for the last 8-10 folders. Even with a good list of bookmarks, it allows getting back to the deeper, remote ones I'm working on at the moment. This is why this display is really good! I wouldn't personally need the access dates or the text box.

Now, something I noticed, the list doesn't refresh when using new folders, so closing and re-opening the list window is necessary to see the newer results. Do you think it would it be possible closing it upon folder opening for example? That would work for me. Again, I tried figuring this out in python, thinking it would not be too complicated haha - I also tried setting up a 'close & open again' shortcut using xdotool, but didn't manage to both the commands working in one go.

EDIT: would you know how to make the folders open with nemo (default file manager) rather than the native file manager?

---

### Post by geofftf on 2020-09-21
What I can do is add a refresh button to the screen. If you press that, program would re-read the .xbel file and generate a fresh list of file paths. Does that sound helpful? I could also provide radio buttons for "Folder Name" and "Folder Path". Would that be helpful?

The MaxDays text box is not doing much now, so I can remove it. It does not even help efficiency, unless the date filter is applied on the first pass through the .xbel file, and we do not appear to have a performance issue anyway.

---

### Post by erza-k-rot on 2020-09-21
Hey geoff, I have figured a workaround for a system-wide refresh shortcut! I'm aware you may view it as a total bloody mess - but at least you can spare the work for this.

First off, I named your script 'recentfolders' and put it in a dedicated folder along with a .sh file in which i wrote:

cd /media/user/.../folder_name
if pgrep -x "python3" > /dev/null
then
    pkill python3 && python3 script_name
else
    python3 recentfolders
fi

(If Python is running, then it kills the process and re-opens the script; otherwise it simply opens it. Of course, this only works if it's the only Python script running.) Then, in the menu editor, I created a launcher which pointed to the .sh file. And finally, I created a new keyboard shortcut pointing towards that launcher I found in ~/.local/share/applications using the gtk-launch command.

However, for the other thing radio buttons would really be *perfect*. Would the default choice be easy to code so it stays? I managed to make the folders open with nemo in your script and am pretty stoked about this too.

---

### Post by geofftf on 2020-09-22
A better solution than a refresh button is to refresh the display whenever the window gains focus. This little script illustrates the process.

```
from tkinter import *
def handle_focus(event):
    if event.widget == root:
        listbox.insert(END, 'X')root = Tk()

listbox = Listbox(root)
listbox.pack()

entry = Entry(root)
entry.pack()

root.bind("<FocusIn>", handle_focus)

root.mainloop()

```

This script adds an 'X' to the listbox every time the window gains focus. I can keep the MaxDays text box and apply the date filter on the first pass through the .xbel file.

---

### Post by geofftf on 2020-09-22
I have modified the program so that the list of paths is refreshed whenever the window gains focus.

```
import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 90

# Named tuple for storage of path name + date entries.
pathdate = namedtuple('pathdate',['path','date'])

# Pruned list of path names and dates extracted from the .xbel file.
Pruned = []

# Event handler for the root window gaining focus.
def handle_focus(event):
    if event.widget == root:
        fill_listbox()

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    global pruned
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar with the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]].path])

# Event handler for <CR> in the entry field.
def on_return_entry(event):
    global MaxDays
    try:
        MaxDays = int(event.widget.get())
    except:
        entry.delete(0, END)
        entry.insert(0, 'Error')
    fill_listbox()

# Event Handler for ^q=quit
def finish(event):
    quit()
    
# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")
# Bind the window gaining focus event to handle.focus
root.bind("<FocusIn>", handle_focus)
# Bind Ctrl-q to finish
root.bind('<Control-q>',finish)

# Create a Frame at the bottom of the root window.
frame = Frame(root)
frame.pack(side=BOTTOM)

# Create a text label on the left of the Frame.
label = Label(frame, text='Maximum days folder accessed before today')
label.pack(side=LEFT)

# Create an entry field on the right of the Frame.
entry = Entry(frame, width=5)
entry.insert(0, str(MaxDays))
entry.bind('<Return>', on_return_entry)
entry.pack(side=RIGHT)

# Create a Listbox and attach it to the left side of the root window.
listbox = Listbox(root, height = 30, width = 60)
listbox.pack(expand=True, side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = Y)
scrollbar.config(command = listbox.yview)
    
# Attach the Listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and a Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
listbox.bind('<Return>',on_click_listbox)
listbox.focus_set()

def fill_listbox():
    
    global MaxDays, Pruned
    
    # Extract the directory path names and modification dates from the recently-used.xbel file.
    mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
    bookmarkNodeList=mydom.getElementsByTagName('bookmark')
    PathDates = []
    for bookmarkNode in bookmarkNodeList:
        filepath=bookmarkNode.getAttribute('href')
        moddate=bookmarkNode.getAttribute('modified')
        fp=urllib.parse.unquote(filepath)[7:]
        if os.path.exists(fp):
            # Use the parser from dateutils to get a datetime from the timestamp string,
            # and then turn that into a date.
            Date = parser.parse(moddate).date()
            if (date.today() - Date).days <= MaxDays:
                PathDates.append(pathdate(os.path.dirname(filepath), Date))

    # Sort PathDates into descending order of path and then modification date.

    # Sort needs a function to give it a key because the list contains complex elements.
    def pd_keyfunc(item):
        return item.path + item.date.strftime("%Y-%m-%d")

    PathDates.sort(reverse=True,key=pd_keyfunc)

    # Each group of duplicate paths is now together in the list, in descending order of date.
    # For each group of duplicate paths, select the first entry for each path from the list,
    # which will be the one with the most recent date.
    Pruned = []
    PrevPath = ''
    for row in PathDates:
        if row.path != PrevPath:
            Pruned.append(row)
            PrevPath = row.path

    # Sort Pruned into descending order of date.

    # Sort needs a function to give it a key because the list contains complex elements.
    def p_keyfunc(item):
        return item.date

    Pruned.sort(reverse=True,key=p_keyfunc)

    # Fill the listbox with the path names with special characters. 
    listbox.delete(0, END)
    for row in Pruned:
        listbox.insert(END, urllib.parse.unquote(row.path[7:]))

root.mainloop()

```

I have had to restructure the program, and it is looking tidier now. I have removed the setting of the list box size based on the maximum path length with the default setting for MaxDays. If we that keep refinement, we should dynamically resize whenever the value of MaxDays changes. I am not sure that is a good idea. I have fixed the problem that partly motivated that change. The scrollbar used to separate from the list box when the window size was increased. That is fixed by using side=LEFT for the scrollbar rather than side=RIGHT. I copied that mistake from a tutorial on Geeks for Geeks.

---

### Post by erza-k-rot on 2020-09-22
This is dangerously approaching perfection there geoff; I certainly think more than a few people will find this helpful. The refresh works amazingly! I really want to thank you for this, it's helping my xubuntu's ergonomy tremendously and I've learned a lot along the way too. I'm still strongly tempted to take you up on your offer to program some radio buttons, but I hope it's not too much to ask! Let me know.

EDIT: I just noticed folders are not sorted by date anymore, is it the same for you?

---

### Post by geofftf on 2020-09-22
Yes, I will put in radio buttons: "Show Folders" and "Show Paths", with Folders as the default. I will also include a checkbox "Show Dates".

I have just checked, and my paths are sorted into descending order of date. You can check that by changing the listbox.insert at (almost) the end of the program to:

listbox.insert(END, row.date.strftime("%Y-%m-%d   ") + urllib.parse.unquote(row.path[7:]))

That will add the modification date to the beginning of each row.

---

### Post by geofftf on 2020-09-24
I have added radio buttons and a check box:

```
# This Python3 program reads the recently-used.xbel file. It extracts the
# directory path names and modification dates. The folder or path names
# (and optionally modification dates) are displayed in a list box.
# The user can select list box entries using either the mouse or the keyboard.
# Thunar is launched each time the user makes a selection.
# The list box entries are refreshed whenever the window gains focus.
# The user can a set a filter for the time window within which entries are
# displayed.

import os
from xml.dom import minidom
from collections import namedtuple
from datetime import date
from dateutil import parser
import urllib.parse
import subprocess
from tkinter import *
import tkinter.messagebox

# Do not show paths that were modified more than MaxDays before today.
MaxDays = 30

# Named tuple for storage of path name + date entries.
pathdate = namedtuple('pathdate',['path','date'])

# Pruned list of path names and modification dates extracted from the .xbel file.
Pruned = []

# Initialise the listbox display options.
show_paths = show_dates = False

# Event handler for the window gaining focus.
def handle_focus(event):
    if event.widget == root: fill_listbox()

# Event handler for Return in the entry field.
def on_return_entry(event):
    global MaxDays
    try:
        MaxDays = int(event.widget.get())
    except:
        tkinter.messagebox.showerror('Error', 'Must be an integer')
    fill_listbox()
    
# Event handler for a radio button selection: "Show Folders" or "Show Paths".
def on_radio_select():
    global show_paths
    show_paths = RadioVar.get()
    fill_listbox()

# Event handler for a check button selection or deselection of "Show Dates".
def on_checkbutton_click():
    global show_dates
    show_dates = CheckVar.get()
    fill_listbox()

# Event handler for a left mouse click on a list box entry.
def on_click_listbox(event):
    # Get the selected line index tuple.
    index = listbox.curselection()
    # Open Thunar with the selected path name.
    subprocess.Popen(['thunar', Pruned[index[0]].path])

# Event Handler for <Ctrl q>.
def finish(event):
    quit()
    
# Create the root window.
root = Tk()
root.title("Recently Accessed Folders")
# Bind the window gaining focus event to handle.focus
root.bind("<FocusIn>", handle_focus)
# Bind <Ctrl q> to finish
root.bind('<Control-q>',finish)

# Create a frame at the bottom of the root window.
frame1 = Frame(root, bd=4)
frame1.pack(side=BOTTOM)

# Create a text label on the left of the Frame.
label = Label(frame1, text='Maximum days folders accessed before today')
label.pack(side=LEFT)

# Create an entry field on the right of the Frame.
entry = Entry(frame1, width=5)
entry.insert(0, str(MaxDays))
entry.bind('<Return>', on_return_entry)
entry.pack(side=RIGHT)

# Create a frame at the bottom of the remaining space within the root window.
frame2 = Frame(root, bd=6)
frame2.pack(side=BOTTOM)

# Create a radio button group with the options "Show Folders" and "Show Paths".
RadioVar = BooleanVar()
radio1 = Radiobutton(frame2, text='Show Folders', variable=RadioVar,
    value=False, command=on_radio_select)
radio1.pack(side=LEFT)
radio2 = Radiobutton(frame2, text='Show Paths', variable=RadioVar,
     value=True, command=on_radio_select)
radio2.pack(side=LEFT)
RadioVar.set(False)

# Create a check box to show the modification date for each row in the listbox.
CheckVar = BooleanVar()
check_button = Checkbutton(frame2, text='Show Dates', variable=CheckVar,
    onvalue=True, offvalue=False, width=15, command=on_checkbutton_click)
check_button.pack(side=LEFT)

# Create a listbox and attach it to the left side of the root window.
listbox = Listbox(root, height = 30, width = 70)
listbox.pack(expand=True, side = LEFT, fill = BOTH)

# Create a Scrollbar and attach it to the right side of the root window.
scrollbar = Scrollbar(root)
scrollbar.pack(side = RIGHT, fill = Y)
scrollbar.config(command = listbox.yview)
    
# Attach the listbox to the Scrollbar.
listbox.config(yscrollcommand = scrollbar.set)

# Bind a left mouse click event and the Return key to the listbox. 
listbox.bind('<ButtonRelease-1>', on_click_listbox)
# Bind the Retuen key to the currently selecetd entry in the listbox.
listbox.bind('<Return>', on_click_listbox)

def fill_listbox():
    
    global MaxDays, Pruned, show_paths, show_dates
    
    # Extract the directory path names and modification dates
    # from the recently-used.xbel file.    
    mydom=minidom.parse(os.environ['HOME'] + '/.local/share/recently-used.xbel')
    bookmarkNodeList=mydom.getElementsByTagName('bookmark')
    PathDates = []
    for bookmarkNode in bookmarkNodeList:
        filepath=bookmarkNode.getAttribute('href')
        moddate=bookmarkNode.getAttribute('modified')
        fp=urllib.parse.unquote(filepath)[7:]
        if os.path.exists(fp):
            # Use the parser from dateutils to get a datetime from the
            # timestamp string, and turn that into a date.
            Date = parser.parse(moddate).date()
            if (date.today() - Date).days <= MaxDays:
                PathDates.append(pathdate(os.path.dirname(filepath), Date))

    # Sort PathDates into descending order of path and then modification date.

    def pd_keyfunc(item):
        return item.path + item.date.strftime("%Y-%m-%d")

    PathDates.sort(reverse=True,key=pd_keyfunc)

    # Each group of duplicate paths is now together in the list, in descending
    # order of date. For each group of duplicate paths, select the first entry
    # for each path from the list, which will be the one with the most recent
    # date.
    Pruned = []
    PrevPath = ''
    for row in PathDates:
        if row.path != PrevPath:
            Pruned.append(row)
            PrevPath = row.path

    # Sort the pruned list into descending order of date.

    def p_keyfunc(item):
        return item.date

    Pruned.sort(reverse=True,key=p_keyfunc)

    # Fill the listbox.
    listbox.delete(0, END)
    for row in Pruned:
        if show_dates:
            outstr = ' ' + row.date.strftime("%Y-%m-%d") + '    '
        else:
            outstr = ' '
        path_name = urllib.parse.unquote(row.path[7:])
        folder_name = path_name[path_name.rindex('/')+1:]
        outstr = outstr + (path_name if show_paths else folder_name)
        listbox.insert(END, ' ' + outstr)
    
    # Set the focus to the listbox.
    listbox.focus_set()
    # Select the first line of the listbox (for <CR>).
    listbox.select_set(0)

root.mainloop()

```

I have also fixed a problem with keyboard selection. The program crashed if the Return key was hit before making a selection with the up an down arrow keys. Xfce does not appear to support keyboard navigation. Neither does Thunar.

---

### Post by erza-k-rot on 2020-09-25
Yesss this is astonishing! Just great great stuff!

I played around with the window size a little bit, opened with nemo by default, and I added the time to this line so they would be displayed by time order:
        return item.path + item.date.strftime("%Y-%m-%d, %H:%M:%S")

I could never thank you enough for your help. You are a very cool person

---

### Post by geofftf on 2020-09-25
Thank you. You are right. It would be better to write the definition of pd_keyfunc as:

```
def pd_keyfunc(item):
    return item.path + item.date.strftime("%Y-%m-%d, %H:%M:%S")
```

The folders should then be in time order to the second.

---

