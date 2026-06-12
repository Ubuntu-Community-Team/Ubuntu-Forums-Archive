---
title: "amule doesnt start anymore...(install uninstall doesnt work)"
date: 2006-06-17
forum: Desktop Environments
---

### Post by tenzin on 2006-06-17
Hi Ubuntuusers,

Since a few day my amule won't start anymore and gives this out:

```
1   tenzin@kalkulator:~$ amule
2   amule: Symbol `_ZTV11wxSpinEvent' has different size in shared object, consider re-linking
3   amule: Symbol `_ZTV14wxTextCtrlBase' has different size in shared object, consider re-linking
4   amule: Symbol `_ZTV16wxDatagramSocket' has different size in shared object, consider re-linking
5   amule: Symbol `_ZTV8wxSlider' has different size in shared object, consider re-linking
6   amule: Symbol `_ZTV14wxSocketServer' has different size in shared object, consider re-linking
7   amule: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
8   amule: Symbol `_ZTV14wxCommandEvent' has different size in shared object, consider re-linking
9   amule: Symbol `_ZTV18wxGenericValidator' has different size in shared object, consider re-linking
10   amule: Symbol `_ZTV20wxNavigationKeyEvent' has different size in shared object, consider re-linking
11   amule: Symbol `_ZTV12wxFocusEvent' has different size in shared object, consider re-linking
12   amule: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
13   amule: Symbol `_ZTV7wxImage' has different size in shared object, consider re-linking
14   amule: Symbol `_ZTV17wxGenericListCtrl' has different size in shared object, consider re-linking
15   amule: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
16   amule: Symbol `_ZTV13wxSocketEvent' has different size in shared object, consider re-linking
17   amule: Symbol `_ZTV10wxTreeCtrl' has different size in shared object, consider re-linking
18   amule: Symbol `_ZTV10wxListItem' has different size in shared object, consider re-linking
19   amule: Symbol `_ZTV12wxTimerEvent' has different size in shared object, consider re-linking
20   amule: Symbol `_ZTV7wxGauge' has different size in shared object, consider re-linking
21   amule: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
22   amule: Symbol `_ZTV10wxRadioBox' has different size in shared object, consider re-linking
23   amule: Symbol `_ZTV8wxChoice' has different size in shared object, consider re-linking
24   amule: Symbol `_ZTV11wxListEvent' has different size in shared object, consider re-linking
25   amule: Symbol `_ZTV11wxImageList' has different size in shared object, consider re-linking
26   amule: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
27   amule: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
28   amule: Symbol `_ZTV13wxNotifyEvent' has different size in shared object, consider re-linking
29   amule: Symbol `_ZTV15wxNotebookEvent' has different size in shared object, consider re-linking
30   amule: Symbol `_ZTV5wxPen' has different size in shared object, consider re-linking
31   amule: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
32   amule: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
33   amule: Symbol `_ZTV16wxZipInputStream' has different size in shared object, consider re-linking
34   amule: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
35   amule: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
36   amule: Symbol `_ZTV10wxTextCtrl' has different size in shared object, consider re-linking
37   amule: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
38   amule: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
39   amule: Symbol `_ZTV12wxCloseEvent' has different size in shared object, consider re-linking
40   amule: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
41   amule: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
42   amule: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
43   amule: Symbol `_ZTV18wxGenericImageList' has different size in shared object, consider re-linking
44   amule: Symbol `_ZTV16wxSplitterWindow' has different size in shared object, consider re-linking
45   amule: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
46   amule: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
47   amule: Symbol `_ZTV7wxBrush' has different size in shared object, consider re-linking
48   amule: Symbol `_ZTV12wxMouseEvent' has different size in shared object, consider re-linking
49   amule: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
50   amule: Symbol `_ZTV10wxListCtrl' has different size in shared object, consider re-linking
51   amule: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
52   amule: Symbol `_ZTV17wxGenericTreeCtrl' has different size in shared object, consider re-linking
53   Segmentation fault
54   tenzin@kalkulator:~$
```

I tried several times to install and uninstall....but it is all the same...

...anybody can help me? 

thx allot!

---

### Post by teclis on 2006-06-17
Have you tried the option in synaptic to completely uninstall amule? You can also try to delete the hidden ".amule"-directory in your HOME or better: rename it. Sometimes this helped me with other programs.

---

### Post by terryman on 2006-06-18
same problem here with amule 2.1.3 and when i try to uninstall amule i get the above error:

```
Removing amule-common ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/ed2k by amule'
  found `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule-utils'
dpkg: error processing amule-common (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 amule-common
```

---

### Post by Jasper Houtman on 2006-06-18
Did you try removing it with the synaptic package manager? That should also be able to remove it if the package is broken.

Was gonna suggest otherwise manually removing, put I checked the install and it  
is spread out to much. So that would be to hard.

If you reinstall make sure that the .Amule directory in your home folder is deleted or renamed first (use Ctrl-H in nautilus).

---

### Post by terryman on 2006-06-18
from synaptic and with the .amule directory renamed, i get the following error:

```
E: amule-common: subprocess post-removal script returned error exit status 2
```

---

### Post by terryman on 2006-06-19
up, just in case someone finds a solution :)

---

### Post by terryman on 2006-06-20
Well i finally managed to uninstall it. 

I first tried to downgrade both amule and amule-common to the 2.12 (earlier) version, through synaptic. The amule-common didnt uninstall but said something about using the terminal with the above command:

```
sudo apt-get install -f
```

I dit that and the amule-common was gone :D

---

### Post by mingotta on 2006-06-24
Have you tried reinstalling it after uninstall?

I currently have Amule CVS (Jan 9, 2006) installed. I don't know if I installed via Automatix or apt-get.
Either way, I'd love to switch to the latest and greatest stable version, that is 2.1.3.
But if I do apt-get install amule it says amule is already the newest version.
Does anybody have a clue??

---

### Post by terryman on 2006-06-25
[QUOTE=mingotta]Have you tried reinstalling it after uninstall?

I currently have Amule CVS (Jan 9, 2006) installed. I don't know if I installed via Automatix or apt-get.
Either way, I'd love to switch to the latest and greatest stable version, that is 2.1.3.
But if I do apt-get install amule it says amule is already the newest version.
Does anybody have a clue??[/QUOTE]

I tried but something went wrong again and i didnt have the time to search and perhaps solve it.

In order to install 2.1.3 you should read [here]("http://forum.amule.org/thread.php?threadid=10281&sid=74d0ee7101c1be087cfaa03922bc7fb5")

---

### Post by mingotta on 2006-06-27
[QUOTE=terryman]In order to install 2.1.3 you should read [here]("http://forum.amule.org/thread.php?threadid=10281&sid=74d0ee7101c1be087cfaa03922bc7fb5")[/QUOTE]

Thanks man, I followed the link you provided and, after some struggle (had to create /etc/ld.so.conf and write /usr/local/lib into it, and then issue ldconfig), I got amule 2.1.3 working on Ubuntu 6.06!!

---

### Post by 3togo on 2006-06-30
[QUOTE=mingotta]Thanks man, I followed the link you provided and, after some struggle (had to create /etc/ld.so.conf and write /usr/local/lib into it, and then issue ldconfig), I got amule 2.1.3 working on Ubuntu 6.06!![/QUOTE]

I guess u need to recomplie the amule all over again. If you are using Edgy rite now, u could download mine.
wget [http://talktomodel.com/~joe/edgy/wxgtk-2.6.3_2.6.3-1_i386.deb](http://talktomodel.com/~joe/edgy/wxgtk-2.6.3_2.6.3-1_i386.deb)
wget [http://talktomodel.com/~joe/edgy/amule-cvs_2.1.3-1_i386.deb](http://talktomodel.com/~joe/edgy/amule-cvs_2.1.3-1_i386.deb)

sudo dpkg -i --force-all wxgtk-2.6.3_2.6.3-1_i386.deb
sudo dpkg -i --force-all amule-cvs_2.1.3-1_i386.deb

---

