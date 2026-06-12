---
title: "using wget to submit form"
date: 2009-04-08
forum: General Help
---

### Post by mike909 on 2009-04-08
I'm trying to use wget to submit a form. I have tried to dig out what is actually being "posted" and where, using tamperdata (see below). 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=109123&stc=1&d=1239224127[/IMG]

Here is my wget command:
```
wget --http-user=xyz --http-password=xyz --post-data='submit_button=Filters&change_action=&submit_type=save&action=Apply&blocked_service=&filter_web=&filter_policy=&f_status=0&services_array=53%3A53%3A17%3ADNS%28%26nbsp%3B%290%3A0%3A1%3APing%28%26nbsp%3B%29443%3A443%3A6%3AHTTPS%28%26nbsp%3B%2921%3A21%3A6%3AFTP%28%26nbsp%3B%29110%3A110%3A6%3APOP3%28%26nbsp%3B%29143%3A143%3A6%3AIMAP%28%26nbsp%3B%2925%3A25%3A6%3ASMTP%28%26nbsp%3B%29119%3A119%3A6%3ANNTP%28%26nbsp%3B%2923%3A23%3A6%3ATelnet%28%26nbsp%3B%29161%3A161%3A17%3ASNMP%28%26nbsp%3B%2969%3A69%3A17%3ATFTP%28%26nbsp%3B%29500%3A500%3A17%3AIKE%28%26nbsp%3B%2980%3A80%3A6%3AHTTP%28%26nbsp%3B%29&services_length=13&service_applist=&blocked_service0=&blocked_service1=&blocked_service2=&blocked_service3=&blocked_service4=&blocked_service5=&blocked_service6=&blocked_service7=&blocked_service8=&blocked_service9=&wait_time=3&start=&f_id=1&f_name=faceboook&f_status1=disable&f_status2=allow&day_all=1&time_all=1&host0=www.facebook.com&host1=&host2=&host3=&url0=facebook&url1=&url3=&url4=&Add_Service_Name=&Add_Service_Port_S=0&Add_Service_Port_E=0&Add_Service_Protocol=23&end=' http://10.0.0.1/Filters.asp
--2009-04-08 13:58:03--  http://10.0.0.1/Filters.asp
Connecting to 10.0.0.1:80... connected.
HTTP request sent, awaiting response... No data received.
Retrying.

```
I can succesfully authenticate to this routers web interface, with the following:
```
wget --keep-session-cookies --http-user=xyz --http-password=xyz http://10.0.0.1/
Connecting to 10.0.0.1:80... connected.
HTTP request sent, awaiting response... 401 Unauthorized
Connecting to 10.0.0.1:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: unspecified [text/html]
Saving to: `index.html.4'

    [   <=>                                                                                                                       ] 73,195       126K/s   in 0.6s    

2009-04-08 14:04:10 (126 KB/s) - `index.html.4' saved [73195]

```

Looking for a hint.

---

### Post by dcstar on 2009-04-09
> **mike909 said:**
> I'm trying to use wget to submit a form. I have tried to dig out what is actually being "posted" and where, using tamperdata (see below). 
........
Looking for a hint.

Are you sure the** ' **delimiter is legal in wget?

---

### Post by mike909 on 2009-04-10
I have tried it with a single ' a double " and also putting the url first (before the --post-date) to no avail. Also tried it without any quote.
Same message.

---

### Post by dcstar on 2009-04-11
> **mike909 said:**
> I have tried it with a single ' a double " and also putting the url first (before the --post-date) to no avail. Also tried it without any quote.
Same message.

Maybe the line is just too long? Try the file option for the data.

---

### Post by mike909 on 2009-04-11
dcstart,
The --post-file option wasn't it entirely, but it did lead me on the right track. Basically, if I use --post-file and change the url to "http://10.0.0.1/apply.cgi" it works.
It dumps an apply.cgi into the working directory, so I need to work on cleaning it up a bit (sending it to > /dev/null maybe) and will update when Ive got it worked out.
Thanks.

---

### Post by dcstar on 2009-04-11
> **mike909 said:**
> dcstart,
The --post-file option wasn't it entirely, but it did lead me on the right track. Basically, if I use --post-file and change the url to "http://10.0.0.1/apply.cgi" it works.
It dumps an apply.cgi into the working directory, so I need to work on cleaning it up a bit (sending it to > /dev/null maybe) and will update when Ive got it worked out.
Thanks.

Persistence pays off......   ;-)

---

### Post by mike909 on 2009-04-14
Ok, the final syntax is as follows:
> wget --auth-no-challenge --output-document=<file_to_contain_output> --timeout=10 --wait=10 --http-user=<user> --http-password=<password> --post-file=<path_to_postfile> [http://10.0.0.1/apply.cgi](http://10.0.0.1/apply.cgi)
Without the --auth-no-challenge, it times out a couple times before worknig. I guess the auth mechanism this interface uses is "old".

edit: how do I change this to "resolved"?

---

