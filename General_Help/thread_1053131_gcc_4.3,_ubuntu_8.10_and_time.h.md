---
title: "gcc 4.3, ubuntu 8.10 and time.h"
date: 2009-01-28
forum: General Help
---

### Post by wish on 2009-01-28
I have been getting segfaults with a pretty basic peice of code. If you take the following:

#include <stdio.h>
#include <stdlib.h>
#include <sys/time.h>

int main()
{
    struct tm *time_rec;
    int time_return;
    const time_t current_time = time(NULL);
    time_rec = localtime(&current_time);
    char* current_date = (char*)malloc(sizeof(char)*10);
    sprintf(
        current_date,
        "%04d-%02d-%02d",
        (time_rec->tm_year + 1900),
        (time_rec->tm_mon + 1),
        time_rec->tm_mday
    );
    printf("%s\n", current_date);
    return 0;
}

and compile it with the -O2 flag, it will cause a segfault. Any ideas why?

---

### Post by wish on 2009-01-28
never mind, my malloc call is wrong.

---

