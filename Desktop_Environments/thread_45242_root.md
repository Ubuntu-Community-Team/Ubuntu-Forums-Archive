---
title: "root"
date: 2005-06-29
forum: Desktop Environments
---

### Post by geist3 on 2005-06-29
I accidentaly did 
sudo chmod 777 * -R
from / i stopped it when it took too long, i was trying to do a directory
Anyway sudo stopped working so I booted into recovery mode and set it to 0440 and it works again
But I can't log in as root, i type in the password and it says setgid: operation not permitted. I'm guessing this is because of a similar reason. Any idea if this can be fixed? I doubt theres a 'rollback' feature to fix all the files i mucked up? Thanks for any support.

---

### Post by jago25_98 on 2005-06-29
Hence the dangers of root. Next time it would have been `chmod -R /foo`

I don't think it can be fixed.

Someone is unlikely to develop something that records the permissions of files in a central database because that sort of person is unlikely to do that mistake.

As far as I can see it's messed up. 

However, it shuold be straightforward because you keep your data (or /home) on in a seporate place... right? If not we'll go through rescuing that

---

### Post by geist3 on 2005-06-29
The file I was changing was in /var/www/mambo/components/moscommerce or something like that, which is why i didnt type it all in. My home files are wherever ubuntu put them by default. I'd rather not toutch root but when i download a file and extract it theyre allways read only and i have to do the sudo thing to make it writeable. It's a good way for me to learn i guess, messing everything up. Just fixing the root login would be good though. Everything else i did guess a re-install would be needed. But i'm sure i should wait until I do damage that makes that mandatory. 
P.S. I dont suppose you know why I get "file save as" dilogue for php files when I access them on my local apache ssl server? (non ssl works fine)

---

### Post by foxy123 on 2005-06-29
[QUOTE=geist3]I accidentaly did 
sudo chmod 777 * -R
from / i stopped it when it took too long, i was trying to do a directory
Anyway sudo stopped working so I booted into recovery mode and set it to 0440 and it works again
But I can't log in as root, i type in the password and it says setgid: operation not permitted. I'm guessing this is because of a similar reason. Any idea if this can be fixed? I doubt theres a 'rollback' feature to fix all the files i mucked up? Thanks for any support.[/QUOTE]
I had the similar problem before: my son being lazy decided to chmod /usr folder. Well, I got a list of permissions and stuff from another user here on the forum with a script to run and change all permissions automatically. Actually it did not help. I managed to reclaim sudo powers but the computer started behaving funny. After a couple of days I just reinstalled Ubuntu from scratch.

---

