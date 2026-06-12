---
title: "Question about rsa base ssh login"
date: 2009-02-06
forum: General Help
---

### Post by ooobooontooo on 2009-02-06
Hi,

I was following the guide to [AdvancedOpenSSH guide]("https://help.ubuntu.com/community/AdvancedOpenSSH"), and had some questions.

I was following it exactly and then used ssh-copy-id to copy the pub key to the remote directory. I definitely provided a passphrase when asked for one. Then when I logged into the remote system after I had copied the key over and it just let me in without asking for the passphrase to the private key...Is that supposed to happen? If not, is that a problem on my side or theirs?

Also, there's not that much difference between dsa and rsa right? From what I've been reading rsa takes longer to generate and is quicker to verify. There's not too much difference in security level right?

In my rsa pub key, it has my login and my hostname...was that supposed to happen? Is that safe...?

Thanks in advance.

---

### Post by geirha on 2009-02-06
> **ooobooontooo said:**
> Hi,

I was following the guide to [AdvancedOpenSSH guide]("https://help.ubuntu.com/community/AdvancedOpenSSH"), and had some questions.

I was following it exactly and then used ssh-copy-id to copy the pub key to the remote directory. I definitely provided a passphrase when asked for one. Then when I logged into the remote system after I had copied the key over and it just let me in without asking for the passphrase to the private key...Is that supposed to happen? If not, is that a problem on my side or theirs?


There's a keyagent/keyring (not sure what keyagent/keyring is used in Ubuntu now adays) where you can put the key. It requires the passphrase to put it there, but once it is there, ssh will let you in without a passphrase. If you log out and then in again, the keyagent/keyring should be empty again, and trying to ssh in should prompt you for the passphrase. 

> **ooobooontooo said:**
> 
Also, there's not that much difference between dsa and rsa right? From what I've been reading rsa takes longer to generate and is quicker to verify. There's not too much difference in security level right?


You should be very safe no matter which you choose :)

> **ooobooontooo said:**
> 
In my rsa pub key, it has my login and my hostname...was that supposed to happen? Is that safe...?

Thanks in advance.

The part behind the two '='s is not part of the key, just a place for comments. You can remove whatever is there if you like, but there's no danger in having it there.

---

### Post by azr on 2009-02-06
I suspect your key-based login may not be configured correctly. It should ask for your pass phrase the first time you login after copying the key over.  

Have you checked the trouble shooting section of the guide? It mentions what to do if not prompted for pass phrase.

---

### Post by ooobooontooo on 2009-02-06
@geirha
I denied all prompts for the keyring thing...I'm thinking of getting rid of it...I don't even know my keyring password... I've never entered any password in there.
Thanks for you clear answer on the second one.
I only have one "=" after the key...is that still considered a comment?

@azr
I thought the troubleshooting guide was for people who are not prompted for their passphrase, but is instead prompted for their username's password like usual. In my case, it didn't prompt for anything and it just let me in. I also looked over the section just in case anyway and everything was in order.

I'm actually starting to suspect something went wrong in the keygen step because I'm getting the same reaction as I would've if I didn't put in any passphrase.

---

### Post by geirha on 2009-02-07
> **ooobooontooo said:**
> @geirha
I denied all prompts for the keyring thing...I'm thinking of getting rid of it...I don't even know my keyring password... I've never entered any password in there.

Try removing the .ssh directory on both the server and client, and try again and see if the same thing happens. ```
ssh user@host "mv ~/.ssh ~/.ssh.old"
mv ~/.ssh ~/.ssh.old
```
> **ooobooontooo said:**
> 
Thanks for you clear answer on the second one.
I only have one "=" after the key...is that still considered a comment?


Yes, it should. I just looked at a random key, which ended with two ==, but now looking at all keys, it seems the == was part of the actual key, and not a delimiter of any kind. space seems to be the only delimiter, and I know you only need the two first fields.

Bad assumption on my part, sorry.

---

### Post by ooobooontooo on 2009-02-07
Wait, I tried ssh-copy-id again and this time it worked...except this time it asks for my keyring thing...How can I get it to just ask for my passphrase to my rsa key? Will it do that if I just delete the keyring thing? Thanks for all your help so far.

---

### Post by geirha on 2009-02-08
If you hit the Cancel button when it wants you to open the keyring, it should ask for the passphrase instead. Not sure if the keyring will pop up again next time you try though.

BTW. You can also handle ssh keys from Applications -> Accessories -> Passwords and Encryption keys.

---

### Post by ooobooontooo on 2009-02-08
No, it asks for the user password not the rsa key passphrase.

Thanks for the tip about the keys.

---

