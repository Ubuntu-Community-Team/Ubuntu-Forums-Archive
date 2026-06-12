---
title: "sudo in debian"
date: 2008-04-04
forum: Debian
---

### Post by cmay on 2008-04-04
hi.
i was jsut wondering about how i can get the debian to work so that i have the same way of using sudo as in ubuntu.
i tried reading a lot but i hav ereal bad eyesight. i am going a bit blind.
however i had debian for two years on my 8 year old computer and only used it for writing a letter and printing that out when i needed to do that. as i erased and forgot all about windows xp 6 month ago 
i use ubuntu now on my new computer for everyday use. i have it dual boot whit 64studio that is also debian based. i play music also.
both ubunut and 64studio lets me use the first account i create when instakling to do sudo apt -get  i am getting used to do this now becouse it is faster than mousing around for the synaptic manager. i have to renember password as well so now time is saved. on my old computer whit debian i have started c programmering as well and i like that debian . i think it is beutifull and i have the 3 dvd so all the debian is right in there in front of me. i simply now when trying to learn debian can not make this work like ubuntu or 64studio whit the sudo thing. no apt -get anything..
is there any on e that could help me out a bit on that one and maybe even tell me a bit more about debian  then i would be very gratefull for the time spendt on this littel subjekt. 
thanks alot.

---

### Post by kerry_s on 2008-04-05
just install sudo->
su
apt-get install sudo

then you need to add yourself to the sudoers file
while your still in root

visudo
or
xedit /etc/sudoers  <(to save, click save 2x)

which ever is easier for you.
put
user    ALL=(ALL) ALL

"user" is your login name

here's what mine looks like.

---

### Post by cmay on 2008-04-05
thank you 
i will wanna go fiddle whit it right after my morning coffe.
by the way do you know about what hte debian default is whit open ports.
i read linux magazine and i had debian sarge before etch
sarge is a bit different than most other linux since there is not a default no open ports on sarge. or so i read .
i like the etch so much for ordinary boring pc work and it was just since i had to do an sudo apr -get some libraries to get geany working  
so i could continue learning c where i left off in windows. i am at pointers now . the time spend on misspelling is about an hour on 30 lines of demo code. however i will learn some day any way.
i am sure i will nerver go back to windows now. i have my doubts about linux sometimes since i dont see as good as i used to do but the ubuntu and debian always work for me so i will wanna learn as much about it as i can now. i might as well its more userfreindly once you know linux and the difference between many "other os" 
anyway thanks for the time and adwise.
i will see if i can get to work.
thank you.

---

### Post by kerry_s on 2008-04-05
you can check your ports here->
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

mine are all closed, i get a true stealth rating.
i'm running etch/lenny custom install, built from the base up.

you can use alias's to save you some typing, i use some for the apt-get stuff.

---

### Post by cmay on 2008-04-05
thanks for the help.
i think i have this etch setup the way i like it to be right now.
this site was pretty interessting reading as well.
i think i will wanna try get a acount at debian users forums  as well  as this ubuntu. i had tried a coupel of days ago but i could not read this code i have to fill in to register . 
this custom install whit debian i tried to do that as well. not building it but just the net install image and then from the base install up to a gnomedesktop .
but i read linuxmagazine and i had to erase the 20 giga byte disk to try out the new distro some time. so i went back to the 3dvd set i have a bit later. i like to see the other distros as well.
i am currently reading andrew s tannnenbaums  book about minix and i bourgt a hard copy of linux from scratch . i like the freedom that linux has . it is worth to fiddle a bit arround whit small issues to get the kind of fredom .
but i am not gonna build my own , just reading about it is good education as well.

well thanks for the support

---

