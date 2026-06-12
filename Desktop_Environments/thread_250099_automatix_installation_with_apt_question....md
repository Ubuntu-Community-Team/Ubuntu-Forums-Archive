---
title: "automatix installation with apt question..."
date: 2006-09-03
forum: Desktop Environments
---

### Post by kpm on 2006-09-03
I posted this on the Automatix forum as well... but what can I say, I am impatient... oh, and stuborn...

I follow the instructions for "Installing with Apt" but when I try to apt-get update I get the following error:
"Malformed line 5 in source list /etc/apt/sources.list (dist)"
Line 5 is "deb http://www.getautomatix.com/apt"
Which is copied directly from the instructions

I then run the following three commands, copied directly from the instructions:
"wget http://www.getautomatix.com/apt/key.gpg.asc"
"gpg --import key.gpg.asc"
"gpg --export --armor 521A9C7C | sudo apt-key add -"

I then run the following two commands, again, copied directly from the instructions:
"sudo apt-get update"
"sudo apt-get install automatix"

and then get the error noted above.

Can anyone help me out on this one... I have installed Automatix before using the installer, but thought I would give apt a try... and being a overly stubborn, I now am stuck on getting it to work with apt rather than scrapping it and just using the installer...

Thanks

---

### Post by Anonii on 2006-09-03
The correct line should be:
_deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main_
replace the line and run the apt-get update again, and then install automatix.

---

### Post by kpm on 2006-09-03
> **Anonii said:**
> The correct line should be:
_deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main_
replace the line and run the apt-get update again, and then install automatix.

Thanks Anonii!
I wonder if that is a typo on the Automatix web site, or just something assumed psuedo sudo newbies like me will know to add on...
EDIT Whooops!  No typo at all... now I see why I didn't copy it correctly... the external link icon set me off and I didn't copy and paste the whole thing... usability getting in the way of usability!

Thanks again.

---

### Post by Anonii on 2006-09-03
Actually I found the line from [http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_Ubuntu_6.06_Dapper_Drake](http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_Ubuntu_6.06_Dapper_Drake). So, maybe you should recheck your sources :3

---

