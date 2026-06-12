---
title: "Increasing font size in Konqueror/Kmail in KDE4 doesn't reflow page"
date: 2008-12-04
forum: Desktop Environments
---

### Post by yodermk on 2008-12-04
Hi,

When I use Ctrl+scroll wheel to jack up the font size, it won't reflow the page. This causes each line to extend well past the screen, forcing a horizontal scroll on each line.

I'm visually impaired and need big fonts, so this is maddening. Especially in KMail. I can set the font size in the settings, and that's fine for plaintext messages. But when I get an HTML message, I can't increase the font size without this effect.

It worked fine in KDE3. If I can't find a solution (I have searched) I may have to switch to Thunderbird (and I *would* like to stick to KMail).

The same happens on my Fedora 10 system at work. Is this a known KDE4 problem?

Thanks for any ideas!

---

### Post by Zorael on 2008-12-04
Sounds like a bug. [Quick, to the launchpadmobile!](https://bugs.launchpad.net/ubuntu) edit: Better yet, [to the bugtrackmobile?](https://bugs.kde.org/)


(Cursory searching yielded no results, but if it's already been reported, the worst thing that can happen is it being tagged as duplicate.)

---

### Post by sayakb on 2008-12-04
@OP
Try Ctrl + (ctrl + plus) and Ctrl - to zoom in/out. Ctrl + help to keep the text wrapped till a certain zoom level.

---

### Post by yodermk on 2008-12-04
Yeah, guess I should file a KDE bug on it since it appears in multiple distros. I certainly want this fixed in KDE 4.2. I can't believe no one else has filed it if it's really a bug. It's pretty "in-your-face" if you need larger fonts. Will do that when I have a few minutes on Saturday.

Ctrl-+ moves me to a message in a different folder, not increases the font size.

---

### Post by sayakb on 2008-12-05
Then try: View -> Enlarge font -> 120 % (or any level that suits you)

---

### Post by yodermk on 2008-12-05
Ah! That does indeed work in Konqueror, thanks!

Unfortunately I don't see a similar option in KMail. :(

---

