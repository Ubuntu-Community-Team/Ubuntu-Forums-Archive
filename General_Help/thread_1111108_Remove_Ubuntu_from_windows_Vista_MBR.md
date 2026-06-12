---
title: "Remove Ubuntu from windows Vista MBR"
date: 2009-03-30
forum: General Help
---

### Post by jordanmoore on 2009-03-30
**[SIZE=5]Intro[/SIZE]**
When i uninstalled ubuntu from my computer i was fustrated, i no longer had ubuntu on the computer but windows' MBR still showed that i had it, after a lot of research i stumbled upon how to remove ubuntu from the MBR so that the computer boots straight into windows. (i have ubuntu on usb now).
 
I figured that i had found no guides on how to remove ubuntu from the Mbr i would create one just incase there is someone else out there with the same problem.
 
 
[SIZE=5]**How to;**[/SIZE]
Step1;
First boot into windows operating system.
 
Step2;
Open the start menu and in the search box type CMD, when it displays the command propmt icon right-click it and press 'Run as administrator'
 
Step3;
When in the cmd type this command in.
'BCDEDIT'
 
Step4;
Look in the list for the Real-mode boot sector, in the section of this down the left column there should be a line that says 'Identifier'.
On the description line if it says UBUNTU then its the right section.
 
Look in the same section for a line of code which looks like this. {cbd971bf-b7b8-4885-951a-fa03044f5d71}
please note i used the windows example code, yours will be different.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108413&d=1238689757[/IMG]
*This image shows what Step 3&4 explain...*
 
Step5;
type this command;
bcdedit /delete {the code you just found} /cleanup
 
Step6;
when you restart, your computer now shouldn't list Ubuntu in the operating systems list.
 
 
 
 
 
 
 
Thats it,
This is my first ever post so be nice.

---

### Post by R.Wise on 2010-01-15
This was a perfect way of uninstalling tried 20 other ways to no avail this one worked perfectly:


[FONT=Verdana][FONT=Verdana]1.[FONT=Times New Roman]     [/FONT][FONT=Verdana]Click **Start**, click **All Programs**, and click **Accessories**.[/FONT][/FONT]
 [FONT=Verdana]2.[FONT=Times New Roman]     [/FONT][FONT=Verdana]Right-click **Command Prompt**, and select **Run as Administrator**.[/FONT][/FONT]
 [FONT=Verdana]3.[FONT=Times New Roman]     [/FONT][FONT=Verdana]Click **Continue** or provide Administrator credentials as prompted.[/FONT][/FONT]
 [FONT=Verdana]4.[FONT=Times New Roman]     [/FONT][FONT=Verdana]Type the **bolded text** and press **Enter** after each one.[/FONT][/FONT]
 [FONT=Verdana] [/FONT]
 [FONT=Courier New]o[FONT=Times New Roman]    [/FONT]*[FONT=Verdana]This command backs up the BCD Store to your Desktop:[/FONT]*[/FONT]
 **[FONT=Verdana] [/FONT]**
 **[FONT=Verdana]BCDEDIT /EXPORT “%HOMEPATH%\DESKTOP\BCDBACKUP”[/FONT]**
 [FONT=Verdana] [/FONT]
 [FONT=Courier New]o[FONT=Times New Roman]    [/FONT]*[FONT=Verdana]This displays the current entries in the BCD Store. Please find the one pertaining to the OS you want to remove from the Boot menu:[/FONT]*[/FONT]
 **[FONT=Verdana] [/FONT]**
 **[FONT=Verdana]BCDEDIT[/FONT]** 
 [FONT=Verdana] [/FONT]
 [FONT=Courier New]o[FONT=Times New Roman]    [/FONT]*[FONT=Verdana]This command deletes the entry from the BCD Store. Replace **{[COLOR=#E36C0A]Identifier[/COLOR]}** with the entry you found in the previous step:[/FONT]*[/FONT]
 **[FONT=Verdana] [/FONT]**
 **[FONT=Verdana]BCDEDIT /DELETE {[COLOR=#E36C0A]Identifier[/COLOR]} /F[/FONT]** 
 [FONT=Verdana] [/FONT]
 [FONT=Verdana]5.[FONT=Times New Roman]     [/FONT][FONT=Verdana]Now restart the computer and the boot entry should be successfully removed from the system.[/FONT][/FONT]

[FONT=Verdana][FONT=Verdana][/FONT][/FONT]
[FONT=Verdana][FONT=Verdana]Just follow these instructions and you are back in business.
[/FONT][/FONT]
[/FONT]

---

### Post by sgage on 2010-01-15
Another way to easily remove (and add) Ubuntu or any other distro from the Windows boot menu is the excellent EasyBCD program from NeoSmart.

[EasyBCD Download]("http://neosmart.net/dl.php?id=1")

---

