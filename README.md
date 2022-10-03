# 安卓 youtube 解除安裝

將 刪除內建yt 的經驗寫下來

使用 OPPO Reno2 Z測試成功:laughing:

---


### 在電腦上使用adb刪除

1. 將手機的 `設定` / `其他設定` / `開發人員選項` / `USB偵錯` 打開

2. 在 [ANDROID STUDIO](https://developer.android.com/studio/releases/platform-tools) 網頁下載 Windows 版 SDK Platform-Tools ( :star:記住你下載的位置 )

3. 下載好後，打開終端機，前往你剛剛下載的位置

    - 比如我的是 : 

      ```
      E:\下載\Compressed\platform-tools_r33.0.3-windows\platform-tools
      ```

4. 用USB線將手機與電腦連接

5. 輸入 `adb devices` 查看是否手機是否有被電腦偵測到

    ```
    E:\下載\Compressed\platform-tools_r33.0.3-windows\platform-tools>adb devices
    List of devices attached
    HQORFYKVKR85G6EU        device # 這樣就是有 
    ```

6. 輸入 `adb shell`，會顯示類似這樣的 : 

    ```
    OP4B65L1:/ $
    ```
    
7. 輸入 `pm list packages` 可以看到手機裡所有packages
    
8. 輸入 `pm list packages| grep 'google'`，會看到所有google app

9. 輸入 `pm uninstall -k --user 0 com.google.android.youtube`，看到Success就代表成功刪除了

    1. 如果沒有成功，先執行這兩行指令 : 

        ```
        pm disable-user com.google.android.youtube
        am force-stop com.google.android.youtube
        ```
        
    2. 再執行一次 `pm uninstall -k --user 0 com.google.android.youtube`

10. 如果再不行可以查看下方的參考網站



---

參考網站 : 

[How to Install and Use ADB, the Android Debug Bridge Utility](https://www.howtogeek.com/125769/how-to-install-and-use-abd-the-android-debug-bridge-utility/)

[ANDROID, DISABLE OR UNINSTALL MORE BLOAT ON NON-ROOTED DEVICES (HERE AN S8)](https://eskerahn.dk/?p=2462)

[How to uninstall apps on android that won't uninstall](https://www.youtube.com/watch?v=KNR1Sf8o2nY)
