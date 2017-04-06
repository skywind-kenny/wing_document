# 天翼畫面API對照表



---
#背景呼叫



app_user_attendance/add_gps_track **(會一直去呼叫)**
system_config/get_version **(會一直去呼叫)**

`android`
app_user_attendance/add_gps_track **(會一直去呼叫)**

---
#登入畫面

system_config/get_version `android`

##登入

app_user_notify/get_count_by_user

app_user/get_targets_by_enterprise
app_user/get_alert_by_number

app_group/get_managers_by_user
app_group/get_groups_by_enterprise (管理者)
app_group/get_group_item

app_user/login
app_user/get_groups

push/save_device_token

schedule/get_targets_by_enterprise
schedule/get_alert_by_number

`android`
app_user/login
app_user/get_groups **(怪 會call兩次)**

app_group/get_managers_by_user
app_group/get_users_by_enterprise_group
app_group/get_allgroups_by_enterprise
app_group/get_group_item

schedule/get_alert_by_number

push/save_device_token

app_user_notify/get_count_by_user



##忘記密碼


app_user/cellphone_check
app_user/active_send_sms

app_user/cellphone_check `android`
app_user/active_send_sms `android`

##填寫驗證碼

app_user/active_verify_sms
app_user/active_verify_sms `android`
**驗證碼填寫過要call甚麼api要確認**

##忘記密碼-送出

app_user/update_secret
app_user/update_secret  `android`

##新用戶註冊

app_user/cellphone_signup

`android`
app_user/cellphone_signup 
system_config/get_config  **(call了兩次分別帶tos跟privacy兩個參數)**




---

#首頁

app_group/get_group_item

app_user_notify/get_count_by_user

`android`

app_user/get_groups
app_user_notify/get_count_by_user
app_group/get_group_item

#首頁_報表

schedule/get_user_type2_report

`android`
schedule/get_user_type2_report

#首頁_任務

schedule/get_by_days

`android`
schedule/get_by_days

**ios每點一天會call一次API，android只會call一次**

###點擊任務進入任務詳細資訊

schedule/get_item_by_id
`android`
schedule/get_item_by_id

###匯報任務

`android`
schedule_mission/update_report
schedule/upload_image (如果有照片)

###群組任務_篩選

`android`
app_group/get_users_by_main_group (會call多次)
app_group/get_users_by_enterprise_group
app_group/get_managers_by_group_id

###群組任務_篩選 選擇成員

`android`
schedule/get_by_days

#首頁_拜訪

###拜訪列表

schedule/get_by_days
`android`
schedule/get_by_days

###點擊拜訪進入拜訪詳細資訊

schedule/get_item_by_id
schedule/get_feedback_by_feedback_id (有回饋資料時)
schedule/set_status_done (按下開始或結束拜訪)
schedule/get_target_by_enterprise (按下開始拜訪)

`android`
schedule/get_item_by_id
schedule/get_feedback_by_feedback_id
contacter/get_company_by_id
contacter/get_company_near_by_gps

###結束拜訪

schedule/set_status_done 
`android`
schedule/set_status_done 
###暫存

schedule/update_feedback
schedule/get_item_by_id
schedule/get_feedback_by_feedback_id

`android`
schedule/set_status_done
schedule/update_feedback
schedule/get_item_by_id
schedule/get_feedback_by_feedback_id


###按下記錄此次拜訪

schedule/set_status_done
schedule/update_feedback
schedule/get_item_by_id (重新刷新頁面)
schedule/get_feedback_by_feedback_id (重新刷新頁面)

`android`
schedule/update_feedback
schedule/set_status_done
schedule/upload_feedback_image
schedule/get_item_by_id
schedule/get_feedback_by_feedback_id

###記錄且下次拜訪

schedule/set_status_done
schedule/update_feedback

`android`
schedule/update_feedback
schedule/set_status_done
schedule/get_item_by_id
schedule/get_targets_by_enterprise

###編輯拜訪
**編輯拜訪未完**
`android`
schedule/update_item
`ios`
schedule/update_item
schedule/set_record_id

**指派人員未完**

`ios`
app_group/get_users_by_enterprise_group (會call多次)
app_group/get_groups_by_enterprise
app_group/get_managers_by_group_id (會call多次)
app_group/get_users (會call多次)

app_user_attendance/get_attendance_flow_by_manager
###聯絡人詳細資訊

`android`
contacter/get_person_by_company_id
contacter/get_company_by_id

---
###新增拜訪

`android`
contacter/get_company_by_user
schedule/get_targets_by_enterprise

###新增拜訪_選擇成員

app_group/get_users_by_enterprise_group
schedule/get_groups_by_enterprise
schedule/get_users
schedule/get_managers_by_group_id
**此地方call了13次api**

`android`
app_group/get_users_by_main_group (會call多次api)
app_group/get_users_by_enterprise_group
app_group/get_managers_by_group_id


####新增拜訪_選擇聯絡人 個人客戶
contacter/get_company_and_user_list

`android`
contacter/get_company_and_user_list

####新增拜訪_選擇聯絡人 企業客戶
####選擇公司

contacter/get_company_and_user_list **(客戶列表)**
contacter/get_person_by_company_id

`android`
contacter/get_company_and_user_list
contacter/get_person_by_company_id (點擊後call)
####選擇文件

document/get_list_by_enterprise
`android`
document/get_list_by_enterprise

###點選文件
schedule/upload_file_enterprise
`android`
schedule/upload_file_enterprise

###新增拜訪完送出
schedule/update_item
schedule/set_record_id
schedule/get_by_days (重新刷新拜訪頁) **會call好幾次api**

`android`
update_item
set_record_id
get_by_days

---

#首頁_日報

###日報列表
app_user_daily/get_list (會call多次api)
`android`
app_user_daily/get_list (會call多次api)
###新增/編輯日報

app_user_daily/update_item
`android`
app_user_daily/update_item

---

#首頁_群組

###群組列表
app_group/get_groups_by_enterprise
`android`
app_group/get_groups_by_enterprise
###點擊群組

app_group/get_managers_by_group_id
app_group/get_subgroups
app_group/get_managers_by_user
app_group/get_users_by_main_group

`android`
app_group/get_managers_by_group_id
app_group/get_users_by_main_group
app_group/get_subgroups

###點擊成員
app_user/get_user `ios`

###新增成員
app_group/get_package_by_enterprise
`android`
app_group/get_package_by_enterprise

###新增成員_確認
app_user/get_users_by_cellphone_batch
send_invite_sms (送出簡訊認證)

###刪除成員
**ios未完**
`android`
user_remove
###新建子群組
**ios未完**
`android`
app_group/update_subgroup

###點擊子群組
**ios未完**
`android`
get_users
get_managers_by_group_id
---

#首頁_消息

###消息列表
app_user_notify/get_list_by_user
`android`
app_user_notify/get_list_by_user

###點擊消息_拜訪
app_user_notify/get_item_by_id (怪 ios任務會call兩次)
app_user_notify/set_status_hide

`android`
app_user_notify/get_item_by_id 
app_user_notify/set_status_hide

以下詳細拜訪資訊
schedule/get_item_by_id
schedule/get_feedback_by_feedback_id
contacter/get_company_by_id
contacter/get_company_near_by_gps

以下為任務
schedule/get_item_by_id

以下為公告
app_user_notify/set_status_hide
app_user_notify/get_item_by_id

以下為考勤
app_user_notify/get_item_by_id
app_user_notify/set_status_hide

---

#日曆

###日曆列表
schedule/get_by_days (ios會call多次)
`android`
schedule/get_by_days 
###詳細內容
同拜訪或任務

事項
schedule/get_item_by_id

###新增行程
schedule/update_item
`android`
schedule/update_item

---

#聯繫

###聯絡人列表

contacter/get_company_and_user_list
`android`
contacter/get_company_and_user_list

###搜尋聯絡人
contacter/get_company_and_user_list
**ios搜尋時沒搜尋內容也會call**
`android`
contacter/get_company_and_user_list

###聯絡人排序
contacter/get_company_and_user_list
`android`
contacter/get_company_and_user_list

###點擊聯絡人
contacter/get_company_by_id
contacter/get_person_by_company_id
`android`
contacter/get_company_by_id
contacter/get_person_by_company_id

###聯絡人相關資訊
contacter/get_research_by_id `ios`

###聯絡人拜訪歷史紀錄
contacter/get_schedules_by_company_id
`android`
contacter/get_schedules_by_company_id
###編輯聯絡人
contacter/update_company
contacter/delete_person
contacter/update_person

`android`
get_company_by_name_batch
update_company
delete_person (如果有刪除的話)
update_person

###新增聯絡人(企業)
contacter/get_company_by_name_batch
contacter/update_company
contacter/update_person

`android`
contacter/get_company_by_name_batch
contacter/update_company
contacter/update_person

###新增聯絡人(個人)

contacter/update_person
`android`
contacter/update_person
---

#考勤


app_user_attendance/get_attendance_flow_by_manager
app_user_attendance/get_log_by_month_with_user
`android`
system_config/get_groups_by_user
app_user_attendance/get_attendance_flow_by_manager
app_user_attendance/get_log_by_month_with_user

###簽到

###簽退

app_user_attendance/get_log_by_month_with_user

`android`
add_attendance
get_log_by_month_with_user

###我的記錄
app_user_attendance/get_log_by_month_with_user (ios會call三次)
`android`
app_user_attendance/get_log_by_month_with_user

###考勤詳細記錄

`android`
get_attendance_by_day

###群組考勤
app_user_attendance/get_attendance_flow_by_manager
`android`
app_user_attendance/get_attendance_flow_by_manager

app_group/get_users_by_main_group (call多次api)
app_group/get_users_by_enterprise_group
app_group/get_managers_by_group_id

###選擇成員

app_user_attendance/get_log_by_month_with_user
`android`
app_user_attendance/get_log_by_month_with_user

---

#文件

document/get_list_by_enterprise
`android`
document/get_list_by_enterprise

###搜尋文件
**ios未完**
`android`
document/search_by_enterprise

---

#設定

`android`
app_user/get_groups
app_group/get_managers_by_user
app_group/get_allgroups_by_enterprise
app_group/get_users_by_enterprise_group

###個人QR code

`android`
system_config/gen_qrcode

###更改姓名

`android`
app_user/update_name

###修改密碼

`android`
app_user/update_secret

###Q&A

`android`
system_config/get_faq

###聯絡skywind

`android`
system_config/get_config
