---
title: "read/write"
date: 2009-02-20
forum: General Help
---

### Post by Lekshmi on 2009-02-20
ssize_t new_read(struct file *filp, int *buf,size_t count, loff_t *f_pos)
        {
                copy_to_user(buf,new_buffer,1);
                printk("<1>Reading Module %d \n",buf[0]);

                if (*f_pos == 0) {
                        *f_pos+=1;
                        return 1;
                } else {
                        return 0;
                        }
        }

ssize_t new_write(struct file *filp, int *buf,size_t count, loff_t *f_pos)
        {
                int *tmp;
                tmp=buf+count-1;
                copy_from_user(new_buffer,tmp,1);
                printk("<1>Writting Module \n");
                return 1;
        }
This is the code for read and write for driver program...i haveto modify this to accept 2 numbers from user and add this then print it...How to modify this? can anyone help?

---

### Post by plucky on 2009-02-20
try the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) sub-forum.

---

