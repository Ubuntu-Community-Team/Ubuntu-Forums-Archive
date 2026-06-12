---
title: "C Script, Count current users and display lowest count"
date: 2009-04-21
forum: General Help
---

### Post by dmitriylm on 2009-04-21
Hey guys, I've been experimenting with some C shell scripting and am in need of help. I'm writing a script that counts the current number of users every minute for fifteen minutes, prints the result to screen and at the end of the cycle displays the lowest number of users of that fifteen minute period. I've got to a point where I can run the fifteen minute interval but I am not sure how to print the lowest figure. 

Here is what I got so far:

#!/bin/csh
# file: usercount
# Count number of users logged onto the user once every minute for fifteen minutes, 
# then print lowest number of users over the course of the past 15 minutes

@ x = 1
set y = `who | wc -l`

while ( $x <= 15 )
	echo "Cycle $x : The number of users is $y"
	@ x++
	sleep 60
end


Here is what I need:

Cycle 1 : number of users = 12
Cycle 2 : number of users = 12
Cycle 3 : number of users = 11
Cycle 4 : number of users = 10
Cycle 5 : number of users = 12
Cycle 6 : number of users = 11
Cycle 7 : number of users = 13
Cycle 8 : number of users = 12
Cycle 9 : number of users = 14
Cycle 10 : number of users = 16
Cycle 11 : number of users = 13
Cycle 12 : number of users = 13
Cycle 13 : number of users = 12
Cycle 14 : number of users = 13
Cycle 15 : number of users = 13


The smallest number of users: 10

---

