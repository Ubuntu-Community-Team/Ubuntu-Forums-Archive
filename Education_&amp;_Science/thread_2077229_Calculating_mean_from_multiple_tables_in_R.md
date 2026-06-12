---
title: "Calculating mean from multiple tables in R"
date: 2012-10-28
forum: Education &amp; Science
---

### Post by ugm6hr on 2012-10-28
Hi

I'm working on genetic sequencing data, and want to calculate mean depth of coverage (value column) by chromosome location (chr and start columns) from multiple samples in R.

Each sample data set is in a text file. e.g.

```
#chr start end value
chr11 2466324 2466325 4
chr11 2466325 2466326 4
chr11 2466326 2466327 5
chr11 2466327 2466328 5
chr11 2466328 2466329 7
chr11 2466329 2466330 7
chr11 2466330 2466331 242
chr11 2466331 2466332 245
chr11 2466332 2466333 245
chr11 2466333 2466334 245
chr11 2466334 2466335 245
chr11 2466335 2466336 245
chr11 2466336 2466337 245
chr11 2466337 2466338 245
...
```

Another example:

```
#chr start end value
chr11 2466606 2466607 60
chr11 2466607 2466608 310
chr11 2466608 2466609 337
chr11 2466609 2466610 337
chr11 2466610 2466611 337
chr11 2466611 2466612 454
chr11 2466612 2466613 465
chr11 2466613 2466614 468
chr11 2466614 2466615 470
...
```

You'll see that the tables do not start in the same location (note start and end locations are different in first data row between 2 files). Nevertheless, the majority of the data refers to the same locations. If necessary, I could manually create 1 file with all the locations (chr / start) that are in all files.

I have ~240 files like those above, each with about 12,000-13,000 lines.

I have no experience of creating loops to import multiple files into R (I have been using bash to call an Rscript to calculate individual logs for this data) - and then am unsure how to import them into the correct rows. 

These are the commands I am aware of:
```
# import 1 table from DepthFile
depthtable <- read.table(DepthFile, quote="")

# how can I import multiple files into this table? 

# calculate means using aggregate table function
meantable <- aggregate.table(depthtable$V4,list(depthtable$V2,depthtable$V3),mean)

# export final table (meantable) to MeanFile
write.table(meantable, MeanFile, sep=" ", quote = FALSE, col.names = FALSE, row.names = FALSE)
```

I need the output file to be similar to above files. i.e. 4 columns of data (headers are irrelevant).

EDIT: I just thought - perhaps I can just concatenate the data files in bash and try the above... Will give that a go and feed back.

---

### Post by ugm6hr on 2012-10-28
Solved:
in bash:
```
cd ~/Documents/bamutil/files/
cat *.text > ../cat_files/depth.text
```

in R:
```

##import cat depth file for depth
depth <- read.table("~/Documents/bamutil/cat_files/depth.text", quote="")

#aggregate values (depth) on chr / start / end values - i.e. form new table with mean depth (value) dependent on columns 1,2,3 (chr,start,end) - suitable for export into circos
meantable <- aggregate(depth$V4,list(depth$V1,depth$V2,depth$V3),mean)

#export mean depth table to mean_depth.text
write.table(meantable, "~/Documents/bamutil/cat_files/mean_depth.text", sep=" ", quote = FALSE, col.names = FALSE, row.names = FALSE)
```

Only outstanding question I am unsure of:
Do the calculated means include a 0 for missing data points (i.e. not present in a table)?
Or is the mean for each site only calculated on those that have a depth recorded?

I think it is the former - but would like to see the table from the latter. I think that FUN=sum in the aggregate command may calculate this, and then I can divide manually by n...

---

### Post by earlycj5 on 2012-10-30
> **ugm6hr said:**
> Hi

I'm working on genetic sequencing data, and want to calculate mean depth of coverage (value column) by chromosome location (chr and start columns) from multiple samples in R.

Each sample data set is in a text file. e.g.

```
#chr start end value
chr11 2466324 2466325 4
chr11 2466325 2466326 4
chr11 2466326 2466327 5
chr11 2466327 2466328 5
chr11 2466328 2466329 7
chr11 2466329 2466330 7
chr11 2466330 2466331 242
chr11 2466331 2466332 245
chr11 2466332 2466333 245
chr11 2466333 2466334 245
chr11 2466334 2466335 245
chr11 2466335 2466336 245
chr11 2466336 2466337 245
chr11 2466337 2466338 245
...
```

Another example:

```
#chr start end value
chr11 2466606 2466607 60
chr11 2466607 2466608 310
chr11 2466608 2466609 337
chr11 2466609 2466610 337
chr11 2466610 2466611 337
chr11 2466611 2466612 454
chr11 2466612 2466613 465
chr11 2466613 2466614 468
chr11 2466614 2466615 470
...
```

You'll see that the tables do not start in the same location (note start and end locations are different in first data row between 2 files). Nevertheless, the majority of the data refers to the same locations. If necessary, I could manually create 1 file with all the locations (chr / start) that are in all files.

I have ~240 files like those above, each with about 12,000-13,000 lines.

I have no experience of creating loops to import multiple files into R (I have been using bash to call an Rscript to calculate individual logs for this data) - and then am unsure how to import them into the correct rows. 

These are the commands I am aware of:
```
# import 1 table from DepthFile
depthtable <- read.table(DepthFile, quote="")

# how can I import multiple files into this table? 

# calculate means using aggregate table function
meantable <- aggregate.table(depthtable$V4,list(depthtable$V2,depthtable$V3),mean)

# export final table (meantable) to MeanFile
write.table(meantable, MeanFile, sep=" ", quote = FALSE, col.names = FALSE, row.names = FALSE)
```

I need the output file to be similar to above files. i.e. 4 columns of data (headers are irrelevant).

EDIT: I just thought - perhaps I can just concatenate the data files in bash and try the above... Will give that a go and feed back.

Why not read each text file and use the merge command?

df <- merge(x, y, by = c('chr', 'start', 'stop')

The loop takes a bit more thinking in order to create a new dataframe each time. I don't have time to noodle on it right now, but if I come up with something I'll post back.

---

