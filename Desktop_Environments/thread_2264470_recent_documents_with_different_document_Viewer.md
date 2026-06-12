---
title: "recent documents with different document Viewer"
date: 2015-02-07
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2015-02-07
Hi,

I have switched to qpdfview as my default document viewer on Ubuntu 14.04 but recent documents no longer getting updated on the Unity dash. How to fix this? Thanks.

I think I have to somehow register qpdfview with zeitgeist.

---

### Post by mc4man on 2015-02-07
Works ok here, seen both in nautilus > recent & Dash > Files and Folders > recent
Have you done anything in the Privacy panel? (haven't here
.local/share/recently-used.xbel should get an entry when you use qpdfview to open a pdf, maybe delete or rename it, open a pdf, then check for an entry.
scr. - top entry opening thru nautilus, bottom entry opening thru qpdfview

---

### Post by monkeybrain20122 on 2015-02-07
Hi,

If I open a document in Nautilis then the recent document list in dash and Nautilis both get updated. But if I search for the same document in the dash and click it to open it doesn't get updated (not in the dash, not in Natilus and not in recently-used-xbel) with evince the list get updated in the second scenario as well.

---

### Post by monkeybrain20122 on 2015-02-07
Looking at recently-used-xbel, the difference is using evince there are entries like 

<bookmark:application name="Document Viewer" exec="&apos;evince %u&apos;" modified="2015-01-14T03:41:57Z" count="7"/>

But qpdfview only get recorded through nautilus
<bookmark:application name="nautilus" exec="&apos;qpdfview --unique %F&apos;" modified="2015-02-08T02:57:08Z" count="2"/>

---

### Post by mc4man on 2015-02-07
I see, so 3 ways with qpdfview set as default  - 
open pdf thru nautilus - writes to recently-used.xbel
open pdf thru qpdfview itself - writes to recently-used.xbel
open pdf from Dash - does not write to recently-used.xbel

So the question is why does a pdf opened via Dash not write to recently-used-xbel with qpdfview but does so with evince?

I wonder if the Dash uses the .desktop or the binary when opening a file? (not that hard to ck., will fool around a bit ..

---

### Post by monkeybrain20122 on 2015-02-07
Yes. If open through qpdfview itself the entry in recently-used-xbel is something like

<bookmark:application name="qpdfview" exec="&apos;qpdfview %u&apos;" modified="2015-02-08T03:51:16Z" count="1"/>

---

### Post by mc4man on 2015-02-07
Ok - so the Dash uses an app's .desktop to open on a file
It could be worth seeing if a modified or custom .desktop would allow writing to the xbel when using the Dash, But - 

Maybe it's because it's a qt4 app??

Test - 
Set some vid type to default open with vlc, open that vid so it will be shown in Dash
Delete recently-used.xbel, leave nautilus open on .local/share
Open Dash > d. click on the vid so it opens in vlc. 
Check & see if recently-used.xbel is re-created.

Result here is it isn't, so it appears that qt4 apps via the Dash don't write to recently-used.xbel

---

### Post by monkeybrain20122 on 2015-02-07
Did the experiment with mpv and it didn't register either. Not sure if mpv is qt.

---

### Post by mc4man on 2015-02-08
Ok, so not qt4. Tested some other apps, ect., many don't write when opened thru Dash
(to d. ck. on mimetype I set evince as default for flac,  an attempt to open a flac in Dash resulted in xbel write & recent entry.

So what sets some apps or app's .desktop apart when open thru Dash ?
(most curious, will try to dig a bit..

---

### Post by mc4man on 2015-02-08
Another ex. set - 
totem does, rhythmbox doesn't..
Maybe the best first look is to see which apps do, it maybe a shorter list that those that don't (by far

---

### Post by monkeybrain20122 on 2015-02-08
I have asked the developer on qpdfview's launchpad page 
[https://answers.launchpad.net/qpdfview/+question/261820](https://answers.launchpad.net/qpdfview/+question/261820)

---

### Post by mc4man on 2015-02-08
Haven't tracked down the actual reason yet - 
Have found that most apps don't write when opened on a file via Dash.

1 clue (maybe) & slight workaround 
Copy qpdfview.desktop to ~/.local/share/applications/ (or any other non writing app's .desktop

Then it should write to the xbel file via Dash

---

### Post by monkeybrain20122 on 2015-02-08
Hi, 

Copied .desktop file to ~/.local/share/applications. Chowned to me and made executable. Logged out and logged back in. Still the same behaviour, open via dash doesn't write to xbel

---

### Post by mc4man on 2015-02-08
> **monkeybrain20122 said:**
> Hi, 

Copied .desktop file to ~/.local/share/applications. Chowned to me and made executable. Logged out and logged back in. Still the same behaviour, open via dash doesn't write to xbel

oops - you're right
(was doing multiple times of various, forgot in the last to open the pdf from Dash, was using nautilus, oh well..

If you ever have future occasion to cp a .desktop to your local applications folder no need to chown or make executable for standard use as a .desktop

---

### Post by mc4man on 2015-02-08
I am fairly pretty sure it's not the .desktop's even though the Dash uses the .desktop or it's Exec= line
(swapped the Exec= in both evince & qpdfview .desktop's to the other app,  the xbel only gets a write from evince even when it's run from qpdfview's .desktop & no xbel when qpdfview is opened from evince's .desktop via the Dash

---

### Post by monkeybrain20122 on 2015-05-07
Seems to be fixed in 15.04.

---

### Post by monkeybrain20122 on 2015-05-09
Opps.Made a mistake, problem still not fixed. I must have done something dumb in the test like opening documents from qdfview instead of dash.

---

### Post by monkeybrain20122 on 2015-05-09
I created a bug report here against unity [https://bugs.launchpad.net/unity/+bug/1453356](https://bugs.launchpad.net/unity/+bug/1453356)

---

