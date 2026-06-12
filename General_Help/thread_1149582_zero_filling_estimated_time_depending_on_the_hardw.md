---
title: "zero filling estimated time depending on the hardware"
date: 2009-05-05
forum: General Help
---

### Post by the_nomad on 2009-05-05
does anyone ever tried before zero filling the harddrive? how long did it take you and what was the configuration you had... ? what program did you use?

here's my configuration:
```
intel quad core @ 2.4 ghz
2 GB RAM
250GB hard drive
```

and i ran in my ubuntu 9.04 live cd (burnt @ 16x) terminal:
```
sudo shred -n 0 -zvv /dev/sda
```

and here are the results after 6 hours:
```
shred: /dev/sda: pass 1/1 (000000)...2.6GiB/233GiB 1%
```

---

### Post by michy99 on 2009-05-05
A 250 Gb drive will take a very long time to fill with zeros (days). Unless you have sensitive data that you don't want anyone to be able to recover, it might be better just to refomat.

---

### Post by Legace on 2009-05-05
Yup, I agree. No idea in that unless you've got very important data. If you really need to get rid of all the data, take a hammer and crash the harddisk.. Or drill holes into it.. :)

---

### Post by the_nomad on 2009-05-05
yeah... would take about 25 days :lolflag:

i guess i'll try to format with gparted :-/ i dont have sensitive data on it.. i just wanted to get rid of all the errors so i wont have to deal with errors soon.. all those errors dont even let me install windows or ubuntu anymore

---

### Post by rbc on 2009-05-05
I used dd to zero out a 500G HD, which took about 17 hours. In my experience, it takes about 2 minutes per GB

---

