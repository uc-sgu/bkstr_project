
<script>
export let session
console.log(session)

//get storeId and detail 
//https://svc.bkstr.com/store/config?storeName=alaskafairbanksstore
//https://svc.bkstr.com/courseMaterial/info?storeId=158904
//https://svc.bkstr.com/courseMaterial/courses?storeId=${storeId}&termId=${termId}

//https://svc.bkstr.com/courseMaterial/results?storeId=509415&langId=-1&catalogId=11077&requestType=DDCSBrowse

//get storeId and detail using first url
//give store id to second url to get terms detail
//give storeid, termid and  get depratment and course
//loop through department and coruse. get object for 10 coruses and get book data for 10 coruse
//keep loop to complete all couress in the store
// start with next school
// Get term 
const storeId=16379;
const termId=100070759;
//"termId":"100070381","termName":"Fall 2021"}],"programId":"1902
const catalogId = 11077;
const department = getDaprtment(storeId,termId);

console.log(JSON.stringify(department))

const course =  getCourses(storeId,catalogId)
const courselist = JSON.stringify(course)
console.log(JSON.stringify(courselist))

async function getDaprtment(storeId,termId) {

const d =  await fetch(`https://svc.bkstr.com/courseMaterial/courses?storeId=${storeId}&termId=${termId}`, {
    method: 'GET',
    mode: 'cors',
    headers: {
		'Accept': 'application/json, text/plain, */*',
        'Content-Type': 'application/json',
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36',
        
        },
    })
    const ret = await d.json();   
    console.log('dpartment');
    console.log(ret.finalDDCSData?.division[0]?.department);
    return ret;  
}

async function getCourses(storeId,catalogId) {
const rest = await fetch(`https://svc.bkstr.com/courseMaterial/results?storeId=${storeId}&langId=-1&requestType=DDCSBrowse`, {
    method: 'POST',
    headers: {
		'Accept': 'application/json, text/plain, */*',
        'Content-Type': 'application/json',
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.159 Safari/537.36',
        
        },
		body: '{"storeId":"166904","termId":"100070759","programId":"2767","courses":[{"secondaryvalues":"AMD/201L/1","divisionDisplayName":"","departmentDisplayName":"AMD","courseDisplayName":"201L","sectionDisplayName":"1"}]}'
    });

    const ret = await rest.json();   
    console.log('course');
    console.log(ret);
    return ret;  
}
</script>
<h1>Profile</h1>
<p> Hello {department} <br>{courselist}

</p>



[{
    "parentStoreId": "166904",
*    "storeId": 166904,
*   "storeNumber": "1202",
*   "storeDisplayName": "Alabama A&M University Bookstore",
    "langId": "-1",
    "locale": "en_US",
    "currency": "USD",
    "requirementTypeLabelMap": {
        "RQ": "Required Material(s)",
        "CH": "Choose - Please select from the following...",
        "RM": "Recommended Material(s)",
        "BR": "Suggested by the Bookstore"
    },
    "materialTypeKeyList": [
        "TXT",
        "CEB",
        "SUP"
    ],
    "isViewByLocation": false,
    "isISBNVisible": true,
    "isHEOACheckAvailabilityLink": true,
    "isSuperSite": false,
    "isEbookStore": true,
    "isShowRental": true,
    "isShowNationalRental": false,
    "isSharedinventory": false,
    "isCourseTrackStore": true,
    "isCourseMaterialPreselected": true,
    "isStoreIncludEDAllStudents": true,
    "isDigitalFeeEnabledStore": true,
    "CRNSearchLevel": "STORE",
    "courseLabel": "Course",
    "sectionLabel": "Section",
    "courseSectionDTO": [{
        "courseSectionStatus": {
            "status": "SUCCESS",
            "code": "0"
        },
      *  "termId": "100070759",
      *  "termName": "FALL 2021",
       * "termNumber": "202170",
        "termStatus": "A",
        "termOpen": true,
        "rentalReturnDate": {
            "year": 2021,
            "month": 11,
            "dayOfMonth": 6,
            "hourOfDay": 0,
            "minute": 0,
            "second": 0
        },
*        "programId": "2767",
 *       "programName": "All",
  *      "campusId": "2252",
   *     "campusName": "Main",
    *    "institutionName": "Alabama A&M University ",
        "ddcsBreadCrumb": "All : FALL 2021 : AMD : 201L : 1",
        "adoptionStatus": "500",
        "courseMaterialResultsList": [{
            "cmId": "8168340469597747",
            "mtcId": "17807348",
     *       "bookImage": "//bkstr.scene7.com/is/image/Bkstr/9781605259970",
       *     "title": "Successful Sewing",
        *    "edition": "N/A",
     8       "author": "Westfall",
      8      "isbn": "9781605259970",
       8     "materialType": "TXT",
       8     "requirementType": "RQ",
            "isbnDisplay": "9781605259970",
            "isPackage": false,
            "priceNewLabel": "FLNew",
            "priceUsedLabel": "FLUsed",
            "newBook": "Y",
            "productCatentryId": "69597747",
            "productPartNumber": "2995acc8-db2c-494c-8004-533d8f57faf9",
        8    "publisherCode": "GW",
         8   "publisherShortName": "GW",
            "copyRightYear": "2013",
          8  "publisher": "Goodheart-Willcox Publisher",
            "messageBookType": 0,
            "preSelected": false,
            "priceRangeDisplay": "$76.00",
            "printItemDTOs": {
                "BUY_NEW": {
                    "typeCondition": "BUY_NEW",
           8         "priceDisplay": "$76.00",
                    "itemCatentryId": "69597748",
                    "inventoryStatusDB": "IN_STOCK",
                    "inventoryStatusBus": "IN_STOCK",
                    "inventoryStatusKey": "INV_IN_STOCK_LABEL",
                    "binding": "PAPERBACK",
                    "preselected": true,
                    "priceNumeric": 76,
                    "availabilityDate": "",
                    "skuPartNumber": "2995acc8-db2c-494c-8004-533d8f57faf9-n",
                    "nonRentalChargesTotal": "$0.00"
                }
            },
            "includEDMaterialFlag": false,
            "titleSelectionDisabled": false
        }],
   8     "division": "",
    8    "divisionName": " ",
        "divisionDescriptorCode": "",
     8   "department": "AMD",
      8  "departmentName": "AMD",
        "departmentDescriptorCode": "AMD",
       8 "course": "201L",
    8    "courseName": "201L",
        "courseDescriptorCode": "201L",
   8     "section": "1",
    8    "sectionName": "1",
        "sectionDescriptorCode": "1",
        "courseId": "81683404",
        "displayFlag": true,
        "salesTrack": "B",
        "courseMinimum": 0,
        "includEdDTO": {
            "isStoreIncludEDAllStudents": true,
            "isIncludEDCampus": false,
            "isIncludEDSection": false,
            "isIncludEDTitle": false
        },

     8   "instructor": "Carmi Bobwealth Omontese",
        "sectionAdoptionDTO": {
            "courseMaterialRelationship": {},
            "materialAdoptions": {
                "REQUIRED": [{
                    "primaryTitleDisplayDTO": {
              8          "title": "Successful Sewing",
               8         "edition": "N/A",
                8        "author": "Westfall",
                 8       "isbn": "9781605259970",
                        "mnpto": 6,
                  8      "bookImage": "//bkstr.scene7.com/is/image/Bkstr/9781605259970",
                        "includEDMaterialFlag": false,
                        "copyrightYear": "2013",
                     8   "publisher": "Goodheart-Willcox Publisher"
                    },
                    "allMaterials": [{
                        "cmId": "8168340469597747",
                        "mtcId": "17807348",
                     8   "bookImage": "//bkstr.scene7.com/is/image/Bkstr/9781605259970",
                      8  "title": "Successful Sewing",
                       8 "edition": "N/A",
                        8"author": "Westfall",
                      8  "isbn": "9781605259970",
                       9 "materialType": "TXT",
                        9"requirementType": "RQ",
                        8"isbnDisplay": "9781605259970",
                        "isPackage": false,
                        "priceNewLabel": "FLNew",
                        "priceUsedLabel": "FLUsed",
                        "newBook": "Y",
                        "productCatentryId": "69597747",
                        "productPartNumber": "2995acc8-db2c-494c-8004-533d8f57faf9",
                       8 "publisherCode": "GW",
                        8"publisherShortName": "GW",
                       8 "copyRightYear": "2013",
                        8"publisher": "Goodheart-Willcox Publisher",
                        "messageBookType": 0,
                        "preSelected": false,
                       8 "priceRangeDisplay": "$76.00",
                        "printItemDTOs": {
                            "BUY_NEW": {
                                "typeCondition": "BUY_NEW",
                                "priceDisplay": "$76.00",
                                "itemCatentryId": "69597748",
                                "inventoryStatusDB": "IN_STOCK",
                                "inventoryStatusBus": "IN_STOCK",
                                "inventoryStatusKey": "INV_IN_STOCK_LABEL",
                                "binding": "PAPERBACK",
                                "preselected": true,
                                "priceNumeric": 76,
                                "availabilityDate": "",
                                "skuPartNumber": "2995acc8-db2c-494c-8004-533d8f57faf9-n",
                                "nonRentalChargesTotal": "$0.00"
                            }
                        },
                        "includEDMaterialFlag": false,
                        "titleSelectionDisabled": false
                    }],
                    "primaryCmId": "8168340469597747",
                    "adoptionType": "INDIVIDUAL"
                }]
            }
        },
        "rentalReturnDateDisplay": "12/6/21"
    }],
    "statusDTO": {
        "status": "SUCCESS",
        "code": "0"
    },
    "homePageURL": "/Home/11077-166904-1?demoKey=d",
    "searchLimit": 0,
    "DDCSBrowseRetentionLevel": "TERM",
    "accordionControl": "ALL_CLOSED",
    "ddcsNotesControl": "NOTES_CLOSED",
    "digitalSurChargeFee": "3.99",
    "summaryProfile": false
}]