---
title: "Installing SuperTuxKart 0.8.1"
date: 2017-01-04
forum: Gaming &amp; Leisure
---

### Post by heroquestelf on 2017-01-04
My laptop cannot handle OpenGL 3. I've tried upgrading my drivers several different ways, and the highest I can get it is to version 2.

That being said, SuperTuxKart 0.9 causes all kinds of graphics issues, where basically I have to reboot the machine every time I play it. 

Before my upgrade to 16.04 I was running STK 0.8.1 without any problems, but when I went to try and reinstall 0.8.1, I get the following error: "Dependency is not satisfiable: supertuxkart-data (=0.8.1-2)"

Is there a way to get the older version to install?

---

### Post by mastablasta on 2017-01-05
how are you installing it? did you download the archive, extract it and then run it?

---

### Post by heroquestelf on 2017-01-05
Okay, I've tried several different downloads. First off I downloaded both the "supertuxkart_0.8.1-2_i386.deb" AND the "supertuxkart_0.8.1-2_amd64.deb". Both of these files give me the above error.

I then downloaded the "supertuxkart-0.8.1-2-linux-glibc2.11-x86-64.tar" file on the SuperTuxKart Sourceforge page. When I unzipped the file, it gave me a folder called "supertuxkart-0.8.1-2-altivec-linux-glibc2.13-ppc".

Inside that folder is a file called "run_game.sh". I clicked on the properties of the file and made sure that the "Allow executing file as program" tab is checked, but it still won't do anything. I've even tried the "Run in terminal" command, which appears to do absolutely nothing.

---

### Post by pme 72 on 2017-01-08
I see a folder "run_game.sh" in my download of 0.9. All I did was enter > supertuxkart in the terminal and the program ran. 

This afternoon I did find a file supertuxkart-0-8-lin-amd64.tar.bz2 on the Sourceforge page, downloaded it to 16.04, extracted the file, opened the folder and clicked on the purple icon named supertuxkart and 0.8 opened and ran. 

Hope you are successful.

---

### Post by heroquestelf on 2017-01-09
I tried running the file in a terminal, I get the following error.

```

jonathan@jonathan-Satellite-P305:~/supertuxkart-0.8.1-2-altivec-linux-glibc2.13-ppc$ ./run_game.sh
./run_game.sh: line 1: bin/supertuxkart: cannot execute binary file: Exec format error
jonathan@jonathan-Satellite-P305:~/supertuxkart-0.8.1-2-altivec-linux-glibc2.13-ppc$ 

```

---

### Post by howefield on 2017-01-09
> **heroquestelf said:**
> Before my upgrade to 16.04 I was running STK 0.8.1 without any problems, but when I went to try and reinstall 0.8.1, I get the following error: "Dependency is not satisfiable: supertuxkart-data (=0.8.1-2)"

You would probably need to install supertuxkart-data_0.8.1-2_all.deb first (and probably also libenet2a) then supertuxkart_0.8.1-2_amd64.deb will most likely install. Because the packages wouldn't come from your installations default repositories I couldn't recommend it but have tried/tested in 16.04 and it does work. But beware of unintended consequences.

---

### Post by mastablasta on 2017-01-11
AFAIK it should work from the tar.gz archive just as *pme72* described.

---

### Post by heroquestelf on 2017-01-14
Ubuntu Support Forums FTW.

You guys rock.

---

### Post by oldrocker99 on 2017-01-17
Since your problem is fixed, please mark this thread as [SOLVED] to help other users.

And thanks for the compliment!

---

