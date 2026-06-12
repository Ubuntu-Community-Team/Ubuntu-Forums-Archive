---
title: "email encryption question"
date: 2009-02-04
forum: General Help
---

### Post by Linux&amp;Gsus on 2009-02-04
Hi @ all,
got a few question about email encryption. If someone can help me or simply point to the right website with the info I'm looking for that would be great.

So far I only played around with GPG very little. The main reason I haven't engaged more is that in fact only 1 person in my entire address book has encryption set up. How bad is that... :(
Anyways, I thought if I finally get fully into it, sign my emails, and explain people what it's all about, then there might be more getting into it. I just don't like the idea that theoretically everybody could read the emails I send to/receive from my family, etc.

Here my first question: Did I understood that correct that I can sign pretty much every email, even if the other person has no encryption set up? Or will they be unable to read the email?

I have a couple, or so, personal email boxes and a bunch of work related boxes. I'm thinking about having 2 different key pairs for these.
Is that a good idea or is that a bit over the top. I just thought that if one key is lost or cracked (or what ever...) then at least not everything is accessible.
So, if I want to have 2 key pairs can I just go through the key generation process twice or will I overwrite something from the first pair? Also, I have not yet found a good tutorial how to set up a key that can be shared by multiple email accounts, any help?

What are the advantages and disadvantages of the different encryption strengths? Obviously besides the having it stronger or weaker. Are there any compatibility issues with older email clients or something like FireGPG, is there a significant difference in speed, etc?

I assume it totally doesn't matter whether I would use POP or IMAP, Yahoo, Gmail, or where ever the emails are hosted, right?

I'm using 2 email clients (Kontact/Kmail and Thunderbird) and different computers. How do I get all the necessary keys to all computers and email clients?

Could I use a key pair that is generated on Linux on a Mac or Windows machine? I have one dual boot machine and a Mac in the office since I need them for testing purposes and would like to be able to get emails there as well.

I read something about backing up the key. They can be exported, or so. But what would be a good advise on how to store them. A thumb drive kinda defeats the purpose. :D But what when something happens on the road, I need to reinstall the machine and need to access that freaking encrypted email? Any ideas on how to store it securely but still having the possibility of accessing it if desperately needed?
E.g. would it be possible to have one thumb drive encrypted with TruCrypt and store some sensitive data, like the key pairs, on there?



Just in case it matters. I have Kubuntu 8.10 w/ KDE4.1 on my main machine. Kubuntu 7.10 w/ KDE 3.5 on an slightly older desktop. Then I have another slightly older machine I use for testing that can run pretty much anything what ever I want, at the moment it's 8.10 as well, but will test 9.04 on there first before using it.


THANKS in advance for any help and insight.

---

### Post by ushills on 2009-02-05
My experience is that I used PGP from the 90's onwards and user use has not really increased from then, people just don't care about encryption that much.

However, I sign all my emails and have found that Thunderbird and the enigmail plugin is a really easy to use system.

Anyone can read signed emails, however, you may want to use PGP/MIME format (an option in enigmail) as this creates a detached signature file rather than inline commenting as provided by default.

For keys I would go with the default that enigmail suggests or you can create them with passwords and encryption within gnome.  Don't forget to create a revocation certificate as you may need this in future, backup both your private and personal keys and keep them somewhere safe away from your main pc.

When you first send out an email to your contacts with your public key attached and upload to a keyserver this may promote the use of gpg and get others using it as well.

You can send a test email to [EMAIL="adele-en@gnupp.de"]adele-en@gnupp.de[/EMAIL] and she will tell you if there are any issue with your keys or setup.

More reading here [http://enigmail.mozdev.org/documentation/quickstart.php](http://enigmail.mozdev.org/documentation/quickstart.php)

---

### Post by ushills on 2009-02-05
You can use gnupg, thunderbird and enigmail on windows and linux and mac and yes use the same keys they are youre personality.

The private key will be secure on a thumb drive as long as you use a secure password and keep a revocation certificate somewhere else that you can use if your key is comprimised.

I keep mine in keepass(win) and keepassx(linux) as they are just text files and can easily be restored from this text

---

### Post by hyper_ch on 2009-02-05
you can sign every mail. It will add some additional data. The recipient can then with your public key verify that it was sent to you. However the email is plaintext.

Normally for each email address you'll have to create a seperate keypair if you want to use ggp/pgp

I don't think you'll have compatibility issues and well, encryption takes longer with a stronger key but as you won't send emails larger than 10mb you won't notice much of a difference.

As long as you can use a mail program to encrypt the emails it does not matter through what service provider you send them.

You'll have to import the keys into your machines and export them from the original one. The keys, if I'm not mistaken, should be stored in /home/USER/.gnugp. You don't have to import the keys in each single email program but the email program must support it. Kontact will by default, for thunderbird you'll need the enigmail extension (and on windows you'll need to install gnugp).

You can use the same keypar on linux, mac, windows.

It is recommended to have a backup. If you want to be truly secure, you will also fully encrypt your OSes that you use. Otherwise an attacker might just get hold of your computer, access the private key and bruteforce the password for it.

On a thumb drive you can use TrueCrypt to create an encrypted file container. This file container can then be mounted, the key stored inside and then umounted. After that it's encrypted. TC works on linux, windows and mac.

---

### Post by Linux&amp;Gsus on 2009-02-05
Hi guys,
thanks for that info. That helps a lot.
I'll get on to that tomorrow probably, since unfortunately and unexpected I don't have the time today.

There is another question, however.
I ran into that app called "KGPG". Is that any helpful? Is there something better?? Or is just simply the best to use the command line???


Thanks and Cheers.

---

### Post by hyper_ch on 2009-02-05
kgpg is for kde

---

### Post by Linux&amp;Gsus on 2009-02-12
I finally got it working. For some reason I had a bit trouble but eventually got it going. 
All I need now is to make sure I have a proper backup.

Thanks heaps for your input guys.

Cheers,
Linux&Gsus


PS: I have KDE :KS as I mentioned in my first post. ;)
My question was more to figure out whether KGPG is a helpful & useful tool or something one should better not touch. Sorry that I didn't make that clear. :oops:

---

