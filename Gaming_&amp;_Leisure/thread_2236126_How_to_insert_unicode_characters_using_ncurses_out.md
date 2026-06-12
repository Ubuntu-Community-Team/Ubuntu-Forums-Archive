---
title: "How to insert unicode characters using ncurses output functions"
date: 2014-07-24
forum: Gaming &amp; Leisure
---

### Post by nemanja3 on 2014-07-24
Hi everyone,

I want to insert unicode characters on terminal using ncurses output functions.

My program:

#include <ncurses.h>
#include <locale.h>
#include <wchar.h>


int main() {
   
   WINDOW* mywin;


   initscr();
   cbreak();
   
   mywin = newwin(8,20,0,0);


   setlocale(LC_ALL ,"");
   wchar_t c = L'\u2588';
   
   wprintw(mywin,"%lc",c);


   wgetch(mywin);
   delwin(mywin);
      
   endwin();
}

I compile with: g++ -o program program.c -lncurses
I got on terminal &#65533;~V~H

---

