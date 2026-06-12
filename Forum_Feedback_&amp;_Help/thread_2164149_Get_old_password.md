---
title: "Get old password"
date: 2013-07-30
forum: Forum Feedback &amp; Help
---

### Post by puzzledinmn on 2013-07-30
Is it possible for me to get my old forum password?  I haven't used the forum since 2008 and I no longer have it.  I would like to know if it is a password that I reused elsewhere.  To log on I had to create a new password for Ubuntu One.  It gave me back my old userid.  Thanks.

---

### Post by lisati on 2013-07-30
If you've got access to your forum account, then I'd suggest changing your password a.s.a.p. - more information in these threads:
[http://ubuntuforums.org/showthread.php?t=2164064](http://ubuntuforums.org/showthread.php?t=2164064)
[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

---

### Post by Elfy on 2013-07-30
Passwords to the forum were all randomised.

Your old password is gone.

---

### Post by deadflowr on 2013-07-30
Change all your passwords anyway.

---

### Post by catslaugh on 2013-07-30
Great. The hackers now have more information than the hacked.

---

### Post by dtuulik on 2013-07-31
How is this SOLVED?? I also want to know what password did I have here, used this forum only once long time ago.. no idea what was the password.

---

### Post by svandragt on 2013-07-31
If a site can email your account password to you, that means the site not storing it securely! 
A site should store a cryptographic representation (hash) of the password, that can be calculated from the password you login with. The calculated hash is then compared with the stored hash.  This hash can not be converted back to your password, this is why your password is not at risk if hackers get to the information. It wouldn't be ethically right for any staff to know passwords of users.

Because of this, unfortunately you will never know what your old password was as it cannot be recovered.

---

### Post by chronicfathead on 2013-07-31
Can anyone give us an idea as to if the old passwords are ever likely to be de-encrypted?

I.e.  If they used a high end PC running flat out it would take a week, month, years, hundreds of years?

How secure was the hash and salt used?

I use Last Pass to store passwords, but unfortunately I didn't have the Ubuntu Forums password in it, so I'm not sure if I've used it elsewhere.  I think it would have been a common password I use for forums, so I have changed several of my other logins at other sites to randomly generated passwords.

---

### Post by NBcsX7h on 2013-07-31
> **chronicfathead said:**
> Can anyone give us an idea as to if the old passwords are ever likely to be de-encrypted?


To be clear, they will not be decrypted, but can be discovered using techniques such as brute force and dictionary attacks. If your password was weak, it may have been discovered very rapidly. [This article]("http://www.wired.co.uk/news/archive/2013-05/28/password-cracking") will give you an idea of just how vulnerable passwords can be in similar circumstances. There are various tools which will allow you to assess the potential strength of your password - [here is one]("http://password-checker.online-domain-tools.com/"). Even if your password was strong, it is advisable to change it if you've used it elsewhere. Truly random passwords may be difficult to memorize - pseudorandom passwords can be strong if they are long enough for the guessability to be sufficiently low. Avoid disguised-word and number combinations, etc., like the plague, and if you want to use diceware combinations of words, use more than four. More-advanced hashing techniques can be beneficial but they're not a panacea.

---

### Post by 7R6Kh6w on 2013-07-31
...strong passwords are difficult to remember, writing it down and safekeep is another hard thing to do and i don't trust password managers either...lol, what are beans anyway...just for brewing coffee i suppose..lol

---

### Post by dxg059 on 2013-07-31
Wow you guys are super awesome at erasing things without thinking.

---

### Post by chronicfathead on 2013-07-31
> **dxg059 said:**
> Wow you guys are super awesome at erasing things without thinking.

Care to elaborate?

They may have used a hammer to crack a walnut by wiping and recreating the forum, but at least we should be safer.  Think of the forum as a beta forum, before the final comes out.

On the passwords, there was no way of finding out what your password was, before or after, due to security.

On the Beans and name front, I think they have said they are trying to get that sorted.

---

### Post by catslaugh on 2013-07-31
If they have a backup of the old password database, it should be possible to set up a simple CGI script that lets you attempt a login to see if the password you input hashes to the one that was in the old database. On success, it tells you that you remembered your old password correctly. That way, you can confirm that you remembered the old password and go change that particular combination on any other sites.

Fortunately for me, Chrome had a copy of that password tucked away in its autofill and I was able to determine that it was a very old password and I only had to dredge up a few disused sites to change it. But other people who are wondering &#8220;was it this old password? this one?&#8221; might benefit from an opportunity to actually check that against the former database.

---

### Post by cariboo on 2013-07-31
I'm really not sure why anyone would want to know what their old no longer available passwords are. If you use one of the utilities available in the repositories to create a password, just create a new one, Two of packages I've used are [apg]("http://www.adel.nursat.kz/apg/") and [pwgen]("http://linux.die.net/man/1/pwgen").

---

