---
title: "Installing Yahoo Messagner"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Eddie Wilson on 2006-07-20
Hello All,
Not sure where to post this question. I've downloaded Yahoo Messagner for linux and tried to install. Has a dependency problem.  Anyone have any luck with this program? Thanks

Iguana

---

### Post by philippe_carlo on 2006-07-20
What exactly did you download? From where? Why do you want the Yahoo client? Isn't Gaim just fine?

---

### Post by Eddie Wilson on 2006-07-20
Downloaded from Yahoo. To get some people to try linux they want their Yahoo Mess. working.

Iguana

---

### Post by philippe_carlo on 2006-07-20
Maybe post the error you get?

---

### Post by byen on 2006-07-20
Ok, I am assuming that you are trying to install the deb that has been provided on yahoo's website. Normally double clicking the downloaded deb package should install the program (via Gdebi installer). If that does not work, You might want to try the following:
Step1: Save the deb file in your home directory
Step2:Open terminal and enter the following
```
sudo dpkg -i packagename.deb
```
And if you get any dependenicy errors, type
```
sudo apt-get -f install
```

The first command installs the program and the second command takes care of the missing dependecies. Try this and let us know.
On a Side note: The messenger provided by Yahoo for linux is way too basic and does not even come close to the features/functionalities of the Windows version. You are better off using Gaim. Just a suggestion.

Hope it helps, Good luck
byen

---

### Post by Eddie Wilson on 2006-07-20
Thank you very much for your help. Getting the missing dependency was where I was having the problem. I'll try it out after work. Again thank you.

Iguana

Gaim is a lot better I know. Its people I'm trying to get to try linux thats wants the Yahoo messenger. Sometimes people are set in their ways at first.

Iguana

---

