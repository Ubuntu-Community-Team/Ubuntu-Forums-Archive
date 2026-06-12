---
title: "Slow disc performance"
date: 2009-05-03
forum: General Help
---

### Post by htoleso on 2009-05-03
I have a very poor drive performance when I copy or move folder with large or small files ( with small files there is a slightly better performance approx. 5MB/s faster ). It doesn't matter if the files are in folder or not, but more the files the slower it gets.

I have two similar hard drives :

first one contains ext3A (20GB), ext3B (80GB) and ntfsC ( 150Gb ) in that order
second one contains linux boot, ntfsA ( 30GB ), ntfsB ( 200GB ) in that order

both should have 30MB/s min, 60MB/s average and 90MB/s top speed ( measured with HD Tune in windows )

Test data : Folder size 4.4 GB ( large files approx. 700MB each)

linux ( gnome nautilus, the speed below are from nautilus and I checked them measuring time and size of the file, they are correct)

ext3B to ntfsC 10MB/s
ext3B to ntfsB 12MB/s
ext3B to ext3A 18MB/s

ext3A to ntfsA 30MB/s
ntfsA to ntfsB 22MB/s
ntfsB to ntfsC 23MB/s

windows ( the speed below is from performance utility, I checked them and they are correct )

ntfsB to ntfsA 30MB/s
ntfsB to ntfsC 50MB/s

Does any one have any similar problems or any solutions?

---

