# Textual-Data-Annotation-Platform
This is portal created using java, jsp, css, bootstrap as frontend and Oracle 10g as backend language in which user can upload textual dataset and also can annotate the datasets available. 

##Create following tables in oracle 10g:
CREATE TABLE  "USERS" 
   (	"EMAIL" VARCHAR2(50), 
	"PASSWORD" VARCHAR2(50), 
	"NAME" VARCHAR2(100), 
	 PRIMARY KEY ("EMAIL") ENABLE
   )


CREATE TABLE  "DATASETS" 
   (	"DATASET_ID" NUMBER(*,0), 
	"DATASET_NAME" VARCHAR2(100), 
	"DATASET_DESC" VARCHAR2(1000), 
	"PATH" VARCHAR2(100), 
	"TOTAL_RECORDS" NUMBER(*,0), 
	"ANNOTATED_RECORDS" NUMBER(*,0), 
	"UPLOADER" VARCHAR2(100), 
	"UPLOAD_DATE" VARCHAR2(100), 
	"DATA_COLUMN" VARCHAR2(50), 
	 PRIMARY KEY ("DATASET_ID") ENABLE
   )
   
CREATE OR REPLACE TRIGGER  "DATASETS_ON_INSERT" 
  BEFORE INSERT ON datasets
  FOR EACH ROW
BEGIN
  SELECT dataset_id_seq.nextval
  INTO :new.dataset_id
  FROM dual;
END;
/
ALTER TRIGGER  "DATASETS_ON_INSERT" ENABLE



CREATE TABLE  "DATASET_LABEL" 
   (	"DATASET_ID" NUMBER, 
	"LABEL" VARCHAR2(50), 
	"LABEL_COUNT" NUMBER
   )


