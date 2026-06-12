---
title: "to Kill only the desktop"
date: 2009-06-01
forum: Desktop Environments
---

### Post by pixel :-) on 2009-06-01
The desktop, by that i mean, only the part with the wallpaper, not the panels, is misbeahaving from time to time. When i drop a file in, it doesn't show up, unless i actually vizit desktop from inside nautilus, worse it just crash, crash nautilus with it, and then everything is gone, the desktop is just the wallpaper.

Whats the program that controls the desktop behaving like a file manager?
So i can do a killall and hopefully restore it. I don't want to restart X because firefox is overloaded with tabs.

Thank you.

---

### Post by kerry_s on 2009-06-01
> **pixel :-) said:**
> The desktop, by that i mean, only the part with the wallpaper, not the panels, is misbeahaving from time to time. When i drop a file in, it doesn't show up, unless i actually vizit desktop from inside nautilus, worse it just crash, crash nautilus with it, and then everything is gone, the desktop is just the wallpaper.

Whats the program that controls the desktop behaving like a file manager?
So i can do a killall and hopefully restore it. I don't want to restart X because firefox is overloaded with tabs.

Thank you.

nautilus is the desktop, sounds like you got some fudged settings.
go in nautilus(the filemanager/Home) press ctrl+h to show hidden folders/files click ".config" look for the nautilus folder and delete it.
close everything and press ctrl+alt+backspace to restart the session with a clean profile. don't just logout or you'll end up with the same thing.

---

### Post by pixel :-) on 2009-06-01
I'll test this when i'll close firefox.

I didn't find nautilus in config, but i find .nautilus in home. I checked modification date, and its indeed the one used and not an old config.

On the other hand, i use a separate partition for home, the content of which is extremely old. It could be some old config file conflicting.

Any way killall nautilus, doesn't unblock it. The problem happens very rarely, and i use hibernate, thus it amounts to a lot of time that the desktop is active.

There isn't something i can kill to restart the  desktop, without killing innocent windows?

---

### Post by MichaelSammels on 2009-06-01
I would say not, since windows are managed by Nautilus. Regarding your speech about old config files - have you tried emptying old/not needed contents of /home?

---

### Post by asmoore82 on 2009-06-01
nautilus is only "file browser" windows and the desktop

it's an easy kill.

---

### Post by pixel :-) on 2009-06-01
> **MichaelSammels said:**
> I would say not, since windows are managed by Nautilus. Regarding your speech about old config files - have you tried emptying old/not needed contents of /home?

You are confusing with metacity. 

ps gives me

nautilus --no-desktop --browser

for standard nautilus, i'm guessing that it crashed but didn't restarted

some one give me the out put of

ps -Af | grep nautilus

Edit, what i said, i found it, i had to run

nautilus -n

---

### Post by pixel :-) on 2009-06-01
How do you edit the title of the thread? I want to add solved.

---

### Post by MichaelSammels on 2009-06-01
Edit your original post and go advanced.

---

### Post by pixel :-) on 2009-06-01
Actually, it only edit the title of the post

it was edit tags down right

---

