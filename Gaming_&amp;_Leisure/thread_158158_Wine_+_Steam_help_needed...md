---
title: "Wine + Steam help needed.."
date: 2006-04-10
forum: Gaming &amp; Leisure
---

### Post by jfx on 2006-04-10
Hi People

I installed Ubuntu, with XGL. Everything works fine, i installed a few games succesfully and not.. the game cube i like, it works very nice..( its funny )
But im addicted to CS 1.6.. so i went and installed wine and winetools setup and everything needed included the fonts, dcom98, installer etc and i didnt had any problems untill i tryed to install steam. The installation goes fine but then i have to update and it hangs everytime at 26% the first few times i got an error [http://solhack.com/files/Screenshot.png]("http://solhack.com/files/Screenshot.png")
i copied the fonts over again then the error didnt appear anymore.. but steam update still hangs at 26%

I can play Doom 3, And Quake 4
I got Ubuntu Dapper (latest)

Thank you for you time and i hope you people can help me out..

greets Juny

---

### Post by thunderduck3141 on 2006-04-10
yeah.....
2 solutions
number one ur network is blocking the updater(find out what port it is trying to use, and forward it)
or
get cedega (its only 15 bucks)

---

### Post by jfx on 2006-04-11
I'm at school now, but ill try the first solution and open the ports in my router as soon as i get home.

for the second solution.. i saw that alot of people got it working with wine and i wan't to try to find a solutions for that first and if im really stuck ill take a look at cedega.. 

are there more thing i can do? or do i need to give some more info?

Greets

---

### Post by jfx on 2006-04-11
I'm no longer behind a firewall or router, and i still got the problem. i looked at the console to see for some errors and i got this:

> waiting for wineservers to exit...
err:menubuilder:extract_icon32 LoadLibraryExW (L"F:\\sys\\\"C:\\Program Files\\Steam\\steam.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"F:\\sys\\http:\\www.steampowered.com\\index.php?area=subscriber_agreement") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:menubuilder:extract_icon32 LoadLibraryExW (L"F:\\sys\\\"C:\\Program Files\\Steam\\unwise.exe\"") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
err:seh:setup_exception stack overflow 88 bytes in thread 0018 eip 7ff94366 esp 7d9abfa8 stack 0x7d9ac000-0x7dabc000
wine: Unhandled page fault on read access to 0x8000007c at address 0x7ff999e3 (thread 001c), starting debugger...
WineDbg starting on pid 0x1b
Unhandled exception: page fault on read access to 0x8000007c in 32-bit code (0x7ff999e3).


and a register dump, and then it freezes again..

can anyone help me with this? Greets

---

### Post by Ferrat on 2006-04-11
This is a know bug with steam, get latest version of wine and you wont have this problem

---

### Post by jfx on 2006-04-11
My bad.. the wine from the ubuntu respo isnt the latest.. i got the latest wine, and now it did continue installing thnx alot..

---

### Post by jfx on 2006-04-11
Well from one problem in to the other.. got steam installed and it updated , but then the steam update screen disappear and it looks like it starting steam again, but then i got this error: [http://solhack.com/files/Screenshot-1.png]("http://solhack.com/files/Screenshot-1.png")

i got close though.. anyone some info or tips :) ill try to find it out myself.. and if i found something ill post it but answers from anyone are welcome..

Greets

---

### Post by thunderduck3141 on 2006-04-11
are u running the program as root
cuz i see that u don't have the correct permissions
try root or using sudo
hope that helps

---

### Post by Ferrat on 2006-04-11
[QUOTE=jfx]Well from one problem in to the other.. got steam installed and it updated , but then the steam update screen disappear and it looks like it starting steam again, but then i got this error: [http://solhack.com/files/Screenshot-1.png]("http://solhack.com/files/Screenshot-1.png")

i got close though.. anyone some info or tips :) ill try to find it out myself.. and if i found something ill post it but answers from anyone are welcome..

Greets[/QUOTE]


nm. not the same problem as me, I get to the loading screen then CSS shutsdown but steam is still running..

---

### Post by jfx on 2006-04-12
I'm not running it as root, but i tryed using sudo.. but got the same error.

anyone?

Juny.!

---

### Post by thunderduck3141 on 2006-04-12
who installed the program (which user i mean)

---

### Post by jfx on 2006-04-13
I got cs running with cedega.. all of you people thnx for the help, leard something though!!!

Greets Juny

---

