---
title: "Steam problems..."
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by RTB-UK on 2006-10-29
Hi im running Ubuntu Edgy 6.10, and I have been trying to get steam installed and running with wine so i can play CS 1.6 and poss CS:S. My first problem is that steam wont run directly from the steam.exe if i run the steam.exe through Nautillus or from the terminal with (sudo/gksudo) ./wine steam.exe it gives me the error:

Steam.exe (main exception):Cannot open blob archive file:
CMultiFieldBlob(mem-mapped file: Failed to MapViewOfFile.

If i create a link to it and run it from my desktop steam starts to update but just sits on 0% then says steam is unavailable. I don't know enough about Linux to know why running it from a link would make a difference. I cant find anyone else with any problem like it :(. Any ideas appreciated.

---

### Post by chameleon_789 on 2006-10-29
Are you running with sudo (or gksudo in gnome)? Sounds like it hasn't got permission to create/access files.

---

### Post by RTB-UK on 2006-10-29
Ive tried running it with sudo and gksudo to no avail. The only way i seem to get it to start is by using a link. Might try reinstalling wine. 

Edit: Reinstall did nothing. Heres an error wine throws up when launching steam directly.

fixme:ntdll:FILE_GetNtStatus Converting errno 19 to STATUS_UNSUCCESSFUL
err:virtual:NtMapViewOfSection map_file_into_view 0x760000 101000 000000000 failed


This seems similar to the steam error ive been getting.

Steam.exe (main exception):Cannot open blob archive file:
CMultiFieldBlob(mem-mapped file: Failed to MapViewOfFile.

---

### Post by gripir-arch on 2006-11-18
Never run wine as root! That is a nono ;)

Do you use ntfs-3g and run your steam from a ntfs partition?

Yes? --> Read the Troubleshooting section number 7 on [linux-gamers.net Steam HowTo]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam")!
Or maybe this link will make it more clear: [Valve Developers Wiki - Steam under Linux]("http://developer.valvesoftware.com/wiki/Steam_under_Linux")

Good luck! :D

---

