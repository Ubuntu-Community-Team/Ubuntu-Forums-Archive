---
title: "cd burning.. please help"
date: 2006-01-12
forum: General Help
---

### Post by drop_d33 on 2006-01-12
hey i need to burn a 700.16mb file into a CDR.. is it possible? i tried it before and i thought everything went well. but when i lent the cdr to my friend, she said the entire movie (the file that i need to burn onto a cd) wasn't recorded, which i know is not possible because as far as i know is that u wont be able to burn a file that doesn't fit on a cd.. how can i burn a 700.16mb file onto CDR and guarantee that the file fits? is there any compression utility that i should use? (and what is the most reliable one?) please help... thanks

---

### Post by SickTwist on 2006-01-12
Compressing it is a good idea. You could try compressing the file with bzip2 or gzip. I do not recommend burning an uncompressed 700+ MB file directly to a CD-R as it might result in a disc that cannot be read by some optical drives.

---

### Post by az on 2006-01-12
If it is a movie, it is already compressed and I doubt you will be able to shrink it more. The compressed file may even be a little bigger!

You can overburn, which means putting more than the maximum allowed size on the cd.  Your burner has to support overburning (and you have to specify that you are overburning) and the cdrom drive that reads it has to be able to read overburned cds, too.

---

### Post by drop_d33 on 2006-01-12
so what should i do? how do i overburn? is it true that u cant burn a file if it wont fit in a cdr? because i was a able to burn it before, but i found out later that the file was not recorded in its entirety. the file is 700.16mb. it is an .avi file, by the way my friend can play avi files in her stand alone dvd player. what should i do?

---

### Post by lamego on 2006-01-12
You can try the command line cdrecord command, look at the man page for it, there is an overburn option.

---

