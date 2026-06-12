---
title: "Not Gettng"
date: 2009-02-19
forum: General Help
---

### Post by Lekshmi on 2009-02-19
This is my driver program that just print the last char of the given string.

i just want to print each character that it reads.

what will i do? 
i gave like printk("<1>Reading Module %s \n",*buf); 
but the output is [172346.895960] Reading Module <NULL>

ssize_t new_read(struct file *filp, char *buf,size_t count, loff_t *f_pos) {
/* Transfering data to user space */
copy_to_user(buf,new_buffer,1);
printk("<1>Reading Module %s \n",*buf);
/* Changing reading position as best suits */
if (*f_pos == 0) {
*f_pos+=1;
return 1;
} else {
return 0;
}
}

ssize_t new_write(struct file *filp, char *buf,
size_t count, loff_t *f_pos) {
char *tmp;
tmp=buf+count-1;
copy_from_user(new_buffer,tmp,1);
printk("<1>Writting Module \n");
return 1;
}

---

### Post by heindsight on 2009-02-19
Perhaps try changing it to
```
printk("<1>Reading Module %s \n", buf);
```

EDIT:
that will print all the contents of buf, up to the first NULL. If you just want the first character then try ```
printk("<1>Reading Module %c \n", buf[0]);
```

---

### Post by Lekshmi on 2009-02-19
ya...........its getting
thank you so...much

---

