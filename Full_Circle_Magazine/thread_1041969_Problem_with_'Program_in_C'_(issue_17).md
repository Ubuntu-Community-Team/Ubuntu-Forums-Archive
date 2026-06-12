---
title: "Problem with 'Program in C' (issue 17)"
date: 2009-01-17
forum: Full Circle Magazine
---

### Post by John Jones on 2009-01-17
I don't know if this is the right forum for this particular problem, but I'm sure somebody will put me right if it isn't

I'm trying to follow the 'Program in C' series which started in issue 17, but I've fallen over at the first hurdle. :cry:

I've entered the 'Hello world' listing in Gedit; -

01. #include <stdio.h>
02.
03. /***********************************
04. * Main function gets called when  * 
05. * the application is launched     *
06. ***********************************/
07. int main()
08. {
09.	// Say something to the audience
10.	printf("Hello world\n");
11.	return 0;
12. }

I can't see anything wrong with what I've typed in, but when I try to compile it, I get the following error messages;-

john@john-desktop:~$ gcc -Wall -W -Werror c-try.c -o c-try
c-try.c:1: error: expected identifier or ‘(’ before numeric constant
c-try.c:1: error: stray ‘#’ in program
john@john-desktop:~$

Out of interest, I installed Anjuta and tried compiling the listing in it; I got the same errors, so presumably there is something wrong with the program I'm trying to compile.

Can anybody help, please. I'm not new to programming, but this has got me beat.

Thanks,

John

---

### Post by ushimitsudoki on 2009-01-17
I just tried that and got the expected output:
> jason@apollo:~$ ./c-try 
Hello world

You aren't actually typing in "01." and "02." and so forth are you?

---

### Post by John Jones on 2009-01-17
[QUOTE=]You aren't actually typing in "01." and "02." and so forth are you?[/QUOTE]

Er, yes I did. I take it I'm not supposed to.

Thanks very much for that, I'll try again.

John:oops:

---

### Post by John Jones on 2009-01-17
It works without the line numbers. Excellent.:)

I haven't seen any other posts regarding this problem, so presumably I'm the only person daft enough to enter the listing as shown, but I'd have thought it would have been a good idea for the author to make it clear in the article that line numbers weren't required. Make it idiot-proof, with me being the idiot in question.

Oh well. Thank goodness for the forum and the people, like yourself, who are good enough to put simpletons like me back on track.

Thanks again.

John

---

### Post by ushimitsudoki on 2009-01-17
Ha ha! No worries, you are quite welcome.

BTW, if you decide to get serious about C, let me suggest [The C Programming Language ]("http://en.wikipedia.org/wiki/The_C_Programming_Language_(book)")by Brian Kernighan and Dennis Ritchie.

This is the book known as "K&R" and is basically the Bible for C - and a darn good primer for programming in general I think.

---

### Post by feelshift on 2009-01-26
You can also start with 'C for Dummies, 2nd edition'. ;)

---

