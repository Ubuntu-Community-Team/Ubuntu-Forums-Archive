---
title: "MySql Backup Script"
date: 2009-05-11
forum: General Help
---

### Post by jwillis44 on 2009-05-11
Here is a script I made to backup my sql databases as well as the www data files. most action items are commented out so that you can change paths passwords etc appropriately. hopefully this will help someone out.

# Joe Willis 5/11/09
# Script to backup mysql databases
# Current databases: check phpmyadmin for dbnames
# in example using folowing:
#     db Name       Discription
#   ------------  ---------------  
#	limesurvey 	- Lime Survey
#	ooz		- One Or Zero Helpdesk Software	
#	tracmor		- TracMor Inventory System
#	wpmu		- Word Press Multi User Blog
#
# Each database will be backed up into a .sql file then ziped.
# The date will be added to the file.
# the www data will be copied into a zip file
#
#
# Starting Script
# 	Set Date
#
	dt=`date +"%d-%m-%y"`
#
#	Set mysql user password  ** MUST BE SET
#	
	DBPASS=*PASSWORD*
#
#	Change to backup directory ** MUST BE SET
	bd=/home/username/path
	cd $bd

#
# Add your mysql databases to be backed up below. 
# 	Lime Survey - DBNAME limeSurvey
#
# UNCOMMENT LINES BELOW
#
# DBNAME=limesurvey
#/usr/bin/mysqldump --opt -u root -p$DBPASS $DBNAME > $DBNAME$dt.sql
#
#	One Or Zero - DBNAME ooz
# DBNAME=ooz
# /usr/bin/mysqldump --opt -u root -p$DBPASS $DBNAME > $DBNAME$dt.sql
#
#	TracMor -DBNAME tracmor
# DBNAME=tracmor
# /usr/bin/mysqldump --opt -u root -p$DBPASS $DBNAME > $DBNAME$dt.sql
#
#	Word Press - DBNAME wpmu
# DBNAME=wpmu
# /usr/bin/mysqldump --opt -u root -p$DBPASS $DBNAME > $DBNAME$dt.sql
#
# copy all .sql files created to .zip file
# Copy www data
# Data paths:
#	lime survey /home/username/path
#	One or Zero /home/username/path
# 	tracmor	    /home/username/path
#	WordPressMU /home/username/path
# Zip up data
#
# 	Change File names as desired below: 
# zip -r $bd/survey_data /home/ooz/www/survey/
# zip -r $bd/ooz_data /home/ooz/www/ooz/
# zip -r $bd/tracmor_data /home/ooz/www/tracmor/
# zip -r $bd/wpmu_data /home/crogers/www/wpmu/
# zip -r sql_backup$dt $bd/*.sql 
#
# now copy to dated folder
mkdir $dt
cp -rf $bd/*.zip $dt
#
# Clean  up
rm $bd/*.sql
rm $bd/*.zip
# end of script

---

