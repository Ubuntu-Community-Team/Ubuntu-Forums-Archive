---
title: "Copying kmenu entries (including names and descriptions)"
date: 2008-05-09
forum: Desktop Environments
---

### Post by Zorael on 2008-05-09
I'm on a laptop which I mostly only use myself, except for a guest login I like to keep for family to use whenever I'm not hogging the machine. So now I'm happy enough with my KDE setup and I thought I'd try to copy my settings to this guest user, to as large an extent as possible.

I began by basically copying the contents of [FONT="Courier New"]~/.kde[/FONT] to [FONT="Courier New"]/home/guest/.kde[/FONT], quickly replacing all occurences of '[FONT="Courier New"]zorael[/FONT]' with '[FONT="Courier New"]guest[/FONT]' in the (textual) files in there. Then I realized I needed to grab [FONT="Courier New"]~/.config/menus[/FONT] to get the kmenu entries transferred, too - but while the menu architecture was transfered, the entry names and descriptions were not.

I even tried copying [FONT="Courier New"]/var/tmp/kdecache-zorael/ksycoca[/FONT] to [FONT="Courier New"]../kdecache-guest/[/FONT] and then doing [FONT="Courier New"]kbuildsycoca[/FONT], but that didn't do anything. I'd really like to avoid having to do this all over again, and keep the entries consistent over both users.


Is there a file I'm missing someplace, that will fix everything?

---

