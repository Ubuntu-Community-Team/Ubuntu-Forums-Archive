---
title: "Evince's 'Send To...' menu"
date: 2017-04-24
forum: Desktop Environments
---

### Post by dulac-will on 2017-04-24
Hi there !I have a desktop computer running Xubuntu 16.04 LTS and I use all the default apps, especially Evince (default Document Viewer program) for reading PDFs and Thunderbird as my mail client.I have this issue with Evince : The 'send to' menu is grayed out, so I did some research and as it turns out, Evince uses nautilus-sendto for this feature and of course XFCE doesn't use Nautilus.So I followed the instructions given here : [https://askubuntu.com/questions/566053/how-to-make-evince-send-to-work-with-thunderbird-in-xubuntu-lts](https://askubuntu.com/questions/566053/how-to-make-evince-send-to-work-with-thunderbird-in-xubuntu-lts) and made both the small script and the /usr/bin/nautilus-sendto symbolic link. And by doing so the 'Send To' menu isn't grayed out anymore, yet Evince denies the permission to run the script.Both the script and the symbolic link depend on the user account (so not root) and have execution permissions (775 for the script itself and lrwxrwxrwx for the symbolic link).I would like to avoid installing nautilus-sendto as it depends on Nautilus and I find that having two file managers is a bit messy.I would appreciate any help on that issue, thank you :-).

---

### Post by ajgreeny on 2017-04-24
I have just tried this out myself and have received exactly the same error as you did.

Interestingly when run in terminal the command in the script does indeed open a TBird compose window but without any attachment actually added, of course.

I have not tried this after restarting my computer but will do so when I get a chance to see if that is necessary; otherwise I do not know quite why it is not working.

---

### Post by dulac-will on 2017-04-24
Hi ajgreeny, thank you for your fast reply !I actually found a solution since earlier:I deleted the symbolic link, renamed the script from "evince-send-to-thunderbird" to "nautilus-sendto" and put it directly into the /usr/bin/ directory, thereby removing the symbolic link intermediary step and Evince now allows me to send my documents with Thunderbird from the menu. In fact I didn't even need to change the script's ownership (meaning it's still 775 but belongs to root:root). I don't know why the symbolic link didn't work but I don't have much experience with these objects either. However, I'm a bit confused by the choice the Xubuntu team made for their default PDF reader given that it's apparently harcoded to be used with GNOME. Now I'm struggling to replace the "Send to" Thunar contextual menu program calling by a similar hack, because the Thunar program that gives the selected file to the system's default mail client fails almost every time to add my PDF as an attachment to Thunderbird for some reason. But at least I'm glad I can now send all my PDFs with Thunderbird using Evince.

---

### Post by ajgreeny on 2017-04-24
Great news and thanks for that info; I did wonder if a symbolic link followed permissions in the usual way but had not so far managed to test this out.

I will now move the script in /opt and see if it now works for me also.  I do not really need it nor will I use it but I am simply interested to see a solution.

EDIT:
Yup!  It also now works for me after using the script itself rather than a symbolic link.

I must look a bit further to fully understand this, but I suspect it is related to the way that symbolic links deal with permissions.

EDIT 2:
I missed your comment about thunar "Send to ->Mail recipient" not working for you; it works fine for me in 16.04 and did also in 14.04.
Perhaps you could do the same job by creating a custom action script; I tried that a few minutes ago and although I can open up the TBird compose window easily enough, I have not managed to get the selected file(s) added as an attachment so far.

---

### Post by dulac-will on 2017-04-25
Yes that's what I'm trying to do. Well it works sometimes, for instance it has no problem adding .jpg files as attachments, but for PDF it's more complicated. Sometimes it works and sometimes the Writing window isn't loaded with the file attached and it is not related to file size. Since I'm sure Thunderbird can take any PDF as an attachment using this type of command seen as the fake nautilus-sendto works for all my documents, I've tried to replace the Exec calling from /usr/share/Thunar/sendto/thunar-sendto-mail.desktop from Thunar's own sending program to something like : thunderbird -compose "attachment='file://%F'" (Because Thunar's send-to program takes %F as an argument, and the correct syntax for a thunderbird attachment is "attachment='file:///path/to/file'". In fact I also found this link: [https://bbs.archlinux.org/viewtopic.php?id=109832](https://bbs.archlinux.org/viewtopic.php?id=109832)) but it doesn't work at all, the Writing window opens but no file is attached, not even the .jpg ones which usually work. So I'm a bit stuck with this I don't quite know how I could make it work. (By the way I'm sorry my posts get shown as one big chunk, I'm going back to line but it's not shown.)

---

### Post by dulac-will on 2017-04-25
Ok I fixed that too. So even though the documented way to send files with Thunderbird via CLI is : thunderbird -compose "attachment='file:///path/to/file'", it turns out Thunderbird is pretty flexible about the syntax. So you can put quotes wherever you want really and it will still work. Now like I said, the 'proper' syntax with %F instead of the /path/to/file didn't work for me so I just replaced the Exec command from the .desktop file with : thunderbird -compose attachment=%F , without any quotes nor 'file://' prefix and it works like a charm. It's still a bit weird because I tested every possible syntax for this command on a dummy test.pdf file and it worked every time, yet they didn't all work for the Mail Recipient contextual menu. But well now all my document-mail-sending issues seem resolved.

---

### Post by ajgreeny on 2017-04-25
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by ajgreeny on 2017-04-25
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

