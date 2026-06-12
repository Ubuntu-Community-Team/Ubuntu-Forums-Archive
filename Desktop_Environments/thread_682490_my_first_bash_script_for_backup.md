---
title: "my first bash script for backup"
date: 2008-01-30
forum: Desktop Environments
---

### Post by penguin steve on 2008-01-30
Hello everyone,

I am new to bash scripting and i decided i wanted to start learning. i decided that a backup script would be of most use to me so i went ahead and searched for tutorials and commands and this is what i came up with.

i know there are a lot of backup scripts out there but i figured i could learn by doing something simple first. i think i kind of got carried away with my script (158 lines) because i saw cool commands and wanted to include them lol. i ended up with a nice layout while it is executed at least. im sure the script could be improved a lot and that im using "echo" way too much but hey, what does it matter if it works right? 

so the two things left that i'd like to include are 
1. support for paths that have spaces. i dont know how to do it because if i specify a path like this "/home/user/backup today" it sees the path "/home/user/backup" and then the "today" command. consequently it returns errors. even if i include quotation marks around the path it still sees it this way. could someone help me out here? 
2. i'd like a progress bar in there somewhere. where can i find these commands? my scrip i have designed from scratch is to backup the /home directory and exclude the ".Trash" folders and other custom folders. remember this is my very first script so i'd like some feedback on what im doing wrong/right and what i can do better next time.

wow if you read all that you deserve a star :KS. lol

thanks for all your help.:guitar:

---

### Post by El_Belgicano on 2008-02-06
Hello,
I'm not an advanced user, but i'd like to learn bash scripting so I took your script as example.
- For your path's, maybe a double quote will solve the problem?
- And for the progress bar you may want to have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=676983").
Nice work :)

---

### Post by penguin steve on 2008-02-06
thanks for your help. i will certainly look at double quotes (thought i tried that but i will again anyway). i have been working on an update to support restore also. thats coming soon. thanks for the link im going to see what i can do with the progress bar. 

if you are looking to learn bash, the site i learned 90% of the bash code in my script is from [this web site](http://www.linuxcommand.org/writing_shell_scripts.php). its very good and the tutorials are great.

ps: i laughed when i clicked on the link in your sig. lol

---

### Post by El_Belgicano on 2008-02-07
for the spaces you have to change the type of the quotes:
'  ' and "  "

'tar cvpzf "/path with spaces/to_some/file" --exclude=/media /home/'

---

### Post by penguin steve on 2008-02-09
thanks for the tip but using 'single quotations' did not work. although the "normal quotations" did so now paths with spaces work flawlessly.
haven't looked at the progress bar code yet but if i include it i will  have to make my script licensed under the same as the progress bar. not sure i want to do that. i think i will stick to my own home brew code.

---

