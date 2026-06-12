---
title: "Photo Upload To Blog"
date: 2009-05-31
forum: General Help
---

### Post by carolina on 2009-05-31
I am using Ubuntu 8.04 and having trouble getting photos uploaded from either my desktop or my documents location to my blog . The blog is using Word Press and when i attempt to upload a photo the dimensions of the image uploads as well as the name of the image to the media library within WP .

 But , when i try to insert the photo all that shows within my blog post is the title and no actual image . Since i am new to Linus i am wondering if there is some application i need to install in order to make photos upload properly ?

---

### Post by Sycron on 2009-05-31
What browser are you using? Can you show us some screenshots?

---

### Post by carolina on 2009-06-07
Sorry i did not get back . I have upgraded to Ubuntu 6.10 but am having a different type of problem with uploading photos .

My word Press application sends me the following when i try and browse to find an image within a file .


**Fatal error**:  Out of memory (allocated 45088768) (tried to allocate 13056 bytes) in **/home/captb/public_html/philippinehomestaytravel.com/wp-admin/includes/image.php** on line [B]147

I have no idea if this a WP issue , a server issue or a Ubuntu issue . Any thoughts ?
[/B]

---

### Post by carolina on 2009-06-16
> **carolina said:**
> Sorry i did not get back . I have upgraded to Ubuntu 6.10 but am having a different type of problem with uploading photos .

My word Press application sends me the following when i try and browse to find an image within a file .


**Fatal error**:  Out of memory (allocated 45088768) (tried to allocate 13056 bytes) in **/home/captb/public_html/philippinehomestaytravel.com/wp-admin/includes/image.php** on line [B]147

I have no idea if this a WP issue , a server issue or a Ubuntu issue . Any thoughts ?
[/B]
THIS ISSUE IS **SOLVED** .  Turns out my lack of experience with F-Spot and digital images in general was the culprit as the file was simply to large and i had to resize the images .

---

