---
title: "Sound problems with Steam"
date: 2005-04-22
forum: Gaming &amp; Leisure
---

### Post by kommissar on 2005-04-22
I have Cedega 4.3.1-1 installed and got it to actually run Steam.  Unfortunately, I have no sound in the game.  I have onboard sound on my motherboard and a Soundblaster Audigy in one of my PCI slots.  I had to install some stuff and then edit /etc/asound.conf  to specify the correct sound card for gnome to play sounds through the right device (is this the correct way to do this??).  How can i get sound in steam?

---

### Post by wbeck85 on 2005-04-22
[QUOTE=kommissar]I have Cedega 4.3.1-1 installed and got it to actually run Steam.  Unfortunately, I have no sound in the game.  I have onboard sound on my motherboard and a Soundblaster Audigy in one of my PCI slots.  I had to install some stuff and then edit /etc/asound.conf  to specify the correct sound card for gnome to play sounds through the right device (is this the correct way to do this??).  How can i get sound in steam?[/QUOTE]
 I think i have a very similar issue. After successfully installing steam via cedega 4.3, I tried to play CS:S. The program initialized but then went to a black screen, as though starting normally, but then a little window pops up saying that the "sound server is already in use", or something similar to that. It gives me a choise to attempt to restart or play without sound (Cancel) I click on cancel and the program just sits there, doing nothing. I have to ctrl+alt+bkspc to get back to gnome. i find it weird. I have also used the /etc/asound.conf method to get system sounds to play.

---

### Post by shakin on 2005-04-22
kommissar: Try plugging your speakers into the other sound card. Cedega might be trying to use the wrong one. If that doesn't work, continue with my suggestion below, although your symptoms are different.

wbeck85: before running the game run 'killall esd'. I almost guarantee that this will work. If after you play the game you no longer have Linux sound, run 'esd'.

---

### Post by Sabator on 2005-04-22
[QUOTE=shakin]kommissar: Try plugging your speakers into the other sound card. Cedega might be trying to use the wrong one. If that doesn't work, continue with my suggestion below, although your symptoms are different.

wbeck85: before running the game run 'killall esd'. I almost guarantee that this will work. If after you play the game you no longer have Linux sound, run 'esd'.[/QUOTE]
 I was told Cedega 4.3 didn't support Steam very well, I downgraded to 4.2 and it works slightly better, but it still takes an age to join a server.

---

### Post by jdodson on 2005-04-22
[QUOTE=Sabator]I was told Cedega 4.3 didn't support Steam very well, I downgraded to 4.2 and it works slightly better, but it still takes an age to join a server.[/QUOTE]

! i downgraded to 4.2 until 4.3.1 came out.  everything works really well with 4.3.1(for me that is).

---

### Post by Sabator on 2005-04-22
It only seems to take ages to join a server the first time, after that I have no problems

---

### Post by kommissar on 2005-04-23
[QUOTE=shakin]kommissar: Try plugging your speakers into the other sound card. Cedega might be trying to use the wrong one. If that doesn't work, continue with my suggestion below, although your symptoms are different.

wbeck85: before running the game run 'killall esd'. I almost guarantee that this will work. If after you play the game you no longer have Linux sound, run 'esd'.[/QUOTE]
Yes, Steam is using the onboard sound.  Does anyone know how to edit the config so that it will use my secondary sound card?

Thanks all!

---

### Post by kommissar on 2005-04-27
I'll give this one last bump before I give up.  Anyone?

---

### Post by sc3252 on 2005-04-27
[QUOTE=kommissar]Yes, Steam is using the onboard sound.  Does anyone know how to edit the config so that it will use my secondary sound card?

Thanks all![/QUOTE]
Did you try turning off the intergrated sound in the bios?

---

### Post by kommissar on 2005-04-27
[QUOTE=sc3252]Did you try turning off the intergrated sound in the bios?[/QUOTE]
Duh... why didn't I think of that earlier.  Thanks SC!

---

