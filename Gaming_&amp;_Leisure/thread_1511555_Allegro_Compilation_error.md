---
title: "Allegro Compilation error"
date: 2010-06-17
forum: Gaming &amp; Leisure
---

### Post by raac on 2010-06-17
Hi, I have posted the same message in "General Help" forum. But then I saw this forum and I thought it will fit better in this one. Anyway please help me with my problem.

 				 				**Allegro compilation** 			
 			 			 		   		 		 		Hi guys I'm  stuck trying to test if the Allegro library is being read correctly,  apparently is not, I need help guys. This is what I've done so far. By  the way I'm new with linux though


I downloaded allegro 4.2.2 from this website..[http://linux.softpedia.com/progDownload/Allegro-Download-295.html](http://linux.softpedia.com/progDownload/Allegro-Download-295.html)

then I looked at the instructions and it said this.. 
//BY THE WAY I DID THIS ON THE FILE ALLEGRO4.2.2 (THE ONE THAT I DOWNLOADED)

Instructions:

 "From here on everything is a pretty standard Unix-style install  process. 
   First you configure it:"

      ./configure

   It should automatically build dependencies. Then you build it:

      make

   And finally you install it (as root -- see below for information on  what
   to do if you can't be root):

      su -c "make install"

   You may also wish to install the man pages:

      su -c "make install-man"

   And perhaps the info docs as well:

      su -c "make install-info"




-----------------------------------------------------------------------------------------------------
Then I typed this program

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <allegro.h>
int main(void){
            char version[80];
            allegro_init();
            sprintf(version, "Allegro library version = %s", allegro_id);
            allegro_message(version);
            allegro_exit();
            return 0;
}
END_OF_MAIN()

-------------------------------------------------------------------------------------------

Then I tried to compile it like this

gcc -Wall -g first.c -o driver

and i get this message

first.c: In function ‘main’:
first.c:9: warning: format not a string literal and no format arguments
/tmp/ccqbhN1i.o: In function `main':
/home/tony/cs/Practice/GAMING/build/first.c:7: undefined reference to  `_install_allegro_version_check'
/home/tony/cs/Practice/GAMING/build/first.c:8: undefined reference to  `allegro_id'
/home/tony/cs/Practice/GAMING/build/first.c:9: undefined reference to  `allegro_message'
/home/tony/cs/Practice/GAMING/build/first.c:10: undefined reference to  `allegro_exit'
collect2: ld returned 1 exit status



THANKS A LOT FOR HELPING ME!!

---

### Post by raac on 2010-06-17
I would appreciate it if you guys also explain me how to compile with g++ for my .cpp files please

---

