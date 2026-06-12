---
title: "Nautilus bug and rights problem"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Xdjibi on 2006-07-14
Hi everybody,

I've encountered a problem yesterday after a system update.

I wanted to move a file using Nautilus (drag'n drop). But the permissions were wrong : I was logged as normal user ghislain and the destination folder was read-only for everybody but the root.

So I modified the permission to give write rights to everybody for this folder.

The folder was open in Nautilus and this modification caused the crash of Nautilus.

I tried to reopen Nautilus and to move my file to the destination folder but Nautilus warned me : move error, you have no write right!!! Followed by  one more Nautilus crash.

So I tried this:
# sudo chown ghislain:ghislain /Destination_folder

And then I retried to move it through Nautilus. Again Nautilus crashed after the warning.

Finally, I moved the file through the console.

But since this episode, the contents of the folder has "disappeared".
There are still five files that are listed through Nautilus but with a zero-byte size!!!

And if I try to list the contents from a console, I get this:
ghislain@Djibix:~$ ls -l Destination_folder/
total 0
?--------- ? ? ? ? ? Destination_folder/file1
?--------- ? ? ? ? ? Destination_folder/file2
?--------- ? ? ? ? ? Destination_folder/file3
?--------- ? ? ? ? ? Destination_folder/file4
?--------- ? ? ? ? ? Destination_folder/file5

Then, if I want to go into Destination_folder, I have :
ghislain@Djibix:~$ cd Destination_folder/
bash: cd: Destination_folder/: Acces denied (translated from french)

But if I check the rights:

ghislain@Djibix:~$ ls -l
drw-rw-rw- 2 ghislain ghislain 4096 2006-07-13 23:37 Destination_folder

I use Dapper 6.06 and Nautilus 2.14.1.


If anybody has an idea or a suggestion, it will be greatly appreciated here!

Thanx in advance,
Djibi

---

