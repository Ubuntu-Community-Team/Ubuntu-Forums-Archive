---
title: "File handling with linux system calls"
date: 2009-04-29
forum: General Help
---

### Post by biebo on 2009-04-29
Can you please guide me about this :

Using Linux/Unix System call, perform following file operations:
1. Create a file
2. Write some string data into the file
3. Read data from one file and copy to another file
4. Get different properties of a file ([COLOR=Red]**size, type, date created and more**[/COLOR])


You may use any programming language but your program should perform all above operations using APIs or system calls. **_Do not use the given library functions of any programming language _**.

i have done the 3rd task with open, read , write functions. the code is :
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>


int main(){


    char block[1024];
    int in,out;
    int reed;

    in = open("/media/Backup/temp/secret.txt",O_RDONLY);
    out = open("/media/Backup/temp/copied.txt",O_WRONLY|O_CREAT,S_IRUSR|S_IWUSR);

    while(  (reed = read(in,block,sizeof(block)))  > 0 ){

        write(out , block , reed);
    }
    return 0;

}

please guide me with rest of the tasks.

thanks

---

### Post by hanzala on 2011-03-08
i think you should use dup2 system call...more you can read on dup2...:popcorn:

pakistan lost the match man :S :S

---

### Post by hanzala on 2011-03-08
and yes read about inode and vnode ...errr where iam taking you :S

---

