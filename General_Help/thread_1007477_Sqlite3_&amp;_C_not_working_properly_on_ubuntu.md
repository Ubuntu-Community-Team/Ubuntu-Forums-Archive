---
title: "Sqlite3 &amp; C not working properly on ubuntu"
date: 2008-12-10
forum: General Help
---

### Post by ckorokeyi on 2008-12-10
I'm trying to use a c program to retrieve information from a sqlite database. The following code compiles and runs with no errors, but does not create the output file that the information from the query yields. In effect... nothing happens when I run it, can anybody see why?


I compile the code with this command:

gcc -lsqlite3 -o trackquery TrackQuery.c


//#include "mex.h"

#include <sqlite3.h>

#include <stdlib.h>

#include <time.h>

#include <sys/types.h>

#include <sys/stat.h>

#include <fcntl.h>

#include <string.h>

#include <stdio.h>



int main (){

	char fname[1024] = "/home/ckorokeyi/Desktop/ MST-04Dec_run04_th9_snsrelim.trk.db";
	char headersOn[16] = ".headers on";
	char modeCSV[16] = ".mode csv";
	char outputFile[32] = ".output TrackQueryCSV.csv";
	char cmd[1024] = "select * from trackdata where trackid = 338;";
	sqlite3* db;

	
	
	//Opens Sqlite3 Database
	if(sqlite3_open(fname, &db)!=SQLITE_OK)
	{
		printf("Error opening database file \n \n");
		return -1;
	}
	printf(" SQLite3 Database Open!\n");

	//Turn headers on
	sqlite3_exec(db,(const char*)headersOn, NULL, NULL, NULL);
	printf(" Headers On!\n");

	//Change output mode to CSV
	sqlite3_exec(db, (const char*)modeCSV, NULL, NULL, NULL);
	printf(" Mode CSV!\n");

	//Set output file name
	sqlite3_exec(db, (const char*)outputFile, NULL, NULL, NULL);
	printf(" Output File TrackQueryCSV!\n");

	//Execute sql query to retrieve track data	
	sqlite3_exec(db, (const char*)cmd, NULL, NULL, NULL);
	printf(" SQL query for track data Executed!\n");


	//Close Sqlite3 Database
	if(sqlite3_close(db)!=SQLITE_OK)
	{
		printf(" Error closing database\n");
		return -1;
	}
	printf(" SQLite3 database closed! \n");
	

	return 0;
}

---

