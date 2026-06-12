---
title: "Hard disk boot failure after Kubuntu 9.04a2 install"
date: 2009-01-14
forum: General Help
---

### Post by nepenthe on 2009-01-14
I tried to install Kubuntu 9.04 Alpha 2 on a 10-GB section right at the end of a 250-GB hard disk. Since manual partioning is officially broken in a2, I chose to install to the largest continuous free space. After install, the computer refused to boot from the hard disk, only printing the "Operating system not found" error message after the BIOS boot screens.

The partitions, though, were perfectly visible, mountable, and readable from an Ubuntu live CD. I have since tried rewriting the MBR, low-level formatting the disk, and re-installing Windows as well as Ubuntu 8.10. After the (consecutive) installs, I still got the same error message upon boot. The new partitions were still visible and readable from a live CD.

After the Ubuntu install, the MBR contained the "GRUB.Geom.Read.Hard Disk.Error". After that, I tried rewriting the MBR using testdisk, and this is what it looks like now:

```

FC 31 C0 8E D0 31 E4 8E D8 8E C0 BE 00 7C BF 00 06 B9 00 01 F3 A5 BE EE 07 B0 08 EA 20 06 00 00 80 3E B3 07 FF 75 04 88 16 B3 07 80 3C 00 74 04 08 06 AF 07 83 EE 10 D0 E8 73 F0 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 BE BE 07 B0 00 B9 04 00 80 3C 00 75 6E FE C0 83 C6 10 E2 F4 31 DB B4 0E BE 9D 07 8A 0E AF 07 AC D0 E9 73 02 CD 10 08 C9 75 F5 B0 3A CD 10 31 C0 CD 16 3C 00 74 F8 BE 8B 07 B9 02 00 E8 BA 00 3C 0D 74 B4 3C 61 72 06 3C 7A 77 02 2C 20 88 C3 BE 9D 07 8A 0E AF 07 AC D0 E9 73 04 38 C3 74 06 08 C9 75 F3 EB AF B8 0D 0E 31 DB CD 10 8D 84 62 00 3C 07 75 07 B0 1F A2 AF 07 EB 99 31 D2 B9 01 00 3C 04 74 11 73 F3 30 E4 B1 04 D2 E0 BE BE 07 01 C6 8A 16 B3 07 BF 05 00 56 F6 C2 80 74 31 B4 41 BB AA 55 52 CD 13 5A 5E 56 72 1E 81 FB 55 AA 75 18 F6 C1 01 74 13 8B 44 08 8B 5C 0A BE 8D 07 89 44 08 89 5C 0A B4 42 EB 0C 8A 74 01 8B 4C 02 B8 01 02 BB 00 7C 50 C6 06 8F 07 01 CD 13 58 5E 73 05 4F 75 B4 EB 93 81 3E FE 7D 55 AA 75 F6 EA 00 7C 00 00 BE 83 07 B9 0A 00 50 B4 0E 31 DB AC CD 10 E2 FB 58 C3 54 65 73 74 44 69 73 6B 0D 0A 10 00 01 00 00 7C 00 00 00 00 00 00 00 00 00 00 31 32 33 34 46 00 00 41 4E 44 54 6D 62 72 00 02 02 02 1F C7 00 00 80 00 00 00 00 00 00 00 00 A5 01 80 01 01 00 83 FE FF FF 3F 00 00 00 C8 CB 2B 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA
```

The only thing I could still try would be to put the hard disk into another machine to see if it will boot there. I might get to that later in the day. In the meantime, any suggestions that I can try while running the live CD would be much appreciated.

TIA

---

### Post by caljohnsmith on 2009-01-14
The Grub stage1 file that gets installed to the MBR has the string "GRUB.Geom.Read.Hard Disk.Error" because those are the errors that the stage1 file can output if something goes wrong, so a Grub MBR will always have that string. In order to get a better idea of what your problem might be, how about booting your Kubuntu CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Kubuntu desktop, open a Konsole and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

