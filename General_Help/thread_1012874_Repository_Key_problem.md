---
title: "Repository Key problem"
date: 2008-12-16
forum: General Help
---

### Post by PrinceArithon on 2008-12-16
OK, so because my semester is over I finally have the time to upgrade to 8.10.  I did a fresh reinstall and all is working fine and dandy.

I hopped over to ubuntuguide.org just to see what is going on for Intrepid...I usually use the guide in case I forgot to install something, reading over it usually helps.

Anyway, I updated the repository with what they have over there and it's fine enough, but I needed the 2 repository keys from Medibuntu and Google.  So here is what I done.

In the terminal I copied and pasted this:

wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O | sudo apt-key add -

Then I got an error that told me this:

wget: option requires an argument -- 'O'
gpg: no valid OpenPGP data found.

So I played with the arguments a bit and took things out, while trying to place other things in.  Nothing really worked.  So I tried the google key and I got the same error.  I can't seem to find anything saying that there is something wrong with keys.  Has anyone else came across this problem??

Anyway here are the keys.

wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O | sudo apt-key add -

wget --quiet [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O | sudo apt-key add -


As I said neither of them worked, and so I'm a little stumped as to what to do.  So far I just commented them out of my source.list file until I can get the keys to work.

Thanks

---

### Post by plucky on 2008-12-16
> wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O | sudo apt-key add -


Try this, use copy and paste into a terminal```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


You are missing a - after the O

Good Luck

---

### Post by PrinceArithon on 2008-12-16
Thanks so much.  I figured if I got a fresh pair of eyes to look at it something would come up.

I was just about to go and try to download the file and then try and run everything after that.

Thank you so much.

---

