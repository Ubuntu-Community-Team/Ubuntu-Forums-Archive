---
title: "High Availability Cluster - File replication and MySQL"
date: 2009-06-24
forum: General Help
---

### Post by AwkwardSilence on 2009-06-24
I am setting up a 4-node web cluster and looking for some suggestions on file replication with user uploaded content. It's not critical to be real-time, but should happen quickly. I've looked at DRBD, but doesn't look like all four nodes can be primaries (only two?). I've only used rsync for simple one-way backups, but haven't looked at it for bi-directional syncing.

What would happen if each node was set up to rsync from the other 3 nodes? Would there be a lot of network congestion and issues with rysnc trying to organize all the new partially written data across the nodes?

Other options I've considered are csync or writing a script that copies files to other nodes when a monitored directory/file is changed. Are there any other packages I should consider before spending time w/ csync, rysnc, or the directory monitoring script?

I'm also looking at master-master replication for MySQL. I've found this article and looks like it should work, but have yet to test it: [http://www.howtoforge.com/setting-up-master-master-replication-on-four-nodes-with-mysql-5-on-debian-etch-p2](http://www.howtoforge.com/setting-up-master-master-replication-on-four-nodes-with-mysql-5-on-debian-etch-p2)

---

### Post by LoneWolfJack on 2009-06-24
are you talking about a DB or a file server? that's not the same.

user uploaded content doesn't go to the database servers in any case though.

what we did for our fileservers was mount several servers via a fibre channel connection as simple directories on our webservers. file distribution is handled by our software, so we can use any 1 node at a time.

as for mysql, take a look at mysql cluster. played around with that thing and if you can build your software to fit, its a brilliant solution.

---

### Post by AwkwardSilence on 2009-06-24
Sorry, the last part probably caused some confusion. I threw the MySQL replication in at the end just to see if anyone had experience with that database replication setup. It is independant of the file replication and I will not be storing any files in the database.

I'm more concerned with file replication at this point. I would like each server to be able to handle file uploads in case one of the nodes went down. Our current setup has a dedicated file server that shares files with our web nodes via NFS. However, if this server went down we would lose our upload capabilites and static content.

---

### Post by LoneWolfJack on 2009-06-24
like I said, we opted for a solution with fiber channel and something like a software server raid, even though our intend was to improve download rates because we're serving almost 1M large (>500kb) image files a day.

what we did was hook up our data servers via fiber channel and mounting them as regular directories (I'll have to ask a tech through what NFS protocol though). now when somebody uploads an image to one of our webservers it will go to the file server with the least load and replication status for this image will be set to 1 in the db. the webserver also keeps a copy of the file.

then we have a little C program that will query the database for images that haven't reached the desired replication level yet and then distribute the respective files among the fileservers. as soon as the desired replication level is reached for an image, the copy on the webserver gets deleted.

this way, we don't have to worry about server failures and we can even take down nodes for maintenance as we like.

as there are reasonable priced 10GB ethernet switches available by now, I wouldn't necessarily rely on fiber channel though. we're considering making the switch as well.

---

