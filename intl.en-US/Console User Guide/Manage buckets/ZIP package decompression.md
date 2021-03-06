# ZIP package decompression

OSS uses Function Compute to automatically decompress ZIP packages that you upload to buckets.

Only ZIP objects can be decompressed in OSS. The following flowchart shows the decompression process.

![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/8867549951/p38103.png)

After you upload ZIP objects to a specified folder in OSS, Function Compute is triggered to automatically decompress the compressed package. Extracted objects are stored in the specified folder in OSS.

## Usage notes

Take note of the following items when you decompress a ZIP package:

-   ZIP package decompression is available in all regions except China \(Heyuan\), China \(Chengdu\), China \(Hong Kong\), Malaysia \(Kuala Lumpur\), UAE \(Dubai\), and UK \(London\).
-   If the package contains object names or folder names that are not UTF-8 or GB 2312 encoded, the object names or folder names after decompression may be garbled, or the decompression process may be interrupted. We recommend that you encode your object names or folder names in UTF-8 and GB 2312.
-   ZIP objects whose storage types are Archive or Cold Archivecannot be decompressed if the objects are in the frozen state. Restore the Archive or Cold Archive objects before you decompress the objects.
-   If decompression takes more than 10 minutes, the ZIP package fails to be decompressed.
-   ZIP package decompression is a value-added service. When a ZIP package is decompressed, Function Compute calculates fees based on the amount of time it takes to decompress the package. For more information, see [Billing methods](https://www.alibabacloud.com/help/zh/doc-detail/54301.htm).

## Procedure

1.  Log on to the [OSS console](https://oss.console.aliyun.com/).

2.  Click **Buckets**, and then click the name of the target bucket.

3.  Choose **Data Processing** \> **Decompress ZIP Package**.

4.  Click **Decompress ZIP Package**.

5.  In the Decompress ZIP Package dialog box, configure the following parameters.

    |Parameter|Description|
    |---------|-----------|
    |**Service Authorization**|To authorize Function Compute to read data from and write data to OSS and execute functions, click **Authorize**.|
    |**Trigger Role**|To authorize OSS to access Function Compute, click **Authorize**. If OSS is authorized to access Function Compute, the **Trigger Role** value is displayed in this section.|
    |**Prefix**|Specifies the prefix that object names must contain to trigger Function Compute. After you set a prefix, Function Compute is triggered when the name of an uploaded object contains the specified prefix. If you set Prefix to abc, Function Compute is triggered when the name of an uploaded object starts with abc or when an object is uploaded to the abc/ folder. **Note:** If this parameter is not set, Function Compute is triggered for all ZIP objects in the bucket. The decompression tasks may be repeatedly run. For more information, see [How to avoid cyclic triggering?](https://www.alibabacloud.com/help/doc-detail/56103.htm). |
    |**Destination Directory**|Specifies the folder where the decompressed ZIP packages are stored. If this parameter is not set, Function Compute decompresses the ZIP packages to the root folder of the current bucket.|

6.  Read and select **I have read the terms of service and agreed to activate Function Compute and process compressed files by using Function Compute. Only file or folder names encoded in UTF-8 or GB 2312 can be processed.** Click **OK**.


## Modify configurations

After you configure ZIP package compression, you can modify the configurations at any time.

1.  Log on to the [OSS console](https://oss.console.aliyun.com/).

2.  Click **Buckets**, and then click the name of the target bucket.

3.  Choose **Data Processing** \> **Decompress ZIP Package**.

4.  Click **Edit** in the Actions column corresponding to the trigger to be modified.

    You can modify the following configurations:

    -   Modify the prefix
        1.  On the **Edit Trigger** page, modify the **Prefix** value in the **Trigger Rule** section. Keep other parameters unchanged.
        2.  Click **OK**.
    -   Modify function configurations
        1.  Click **OK**.
        2.  Click **Overview**. On the Overview tab, click **Configure**.
        3.  On the **Configure Function** page, modify the function configurations.

            You can modify the values of the **Memory**, **Timeout**, and **Environment Variables** parameters:

            -   **Memory**: You can configure this parameter based on the size of the object to be processed. If the size of the ZIP package is small, set this parameter to a small value to save costs when the function is executed.
            -   **Timeout**: A timeout error is displayed if the function cannot be executed during the specified period. We recommend that you configure an appropriate timeout period to avoid timeout during function execution.
            -   **Environment Variables**: If you modify this parameter value, the destination directory of the extracted objects is modified.
        4.  Click **Submit**.

## Delete configurations

You can manually delete unnecessary configurations for Function Compute.

1.  Log on to the [OSS console](https://oss.console.aliyun.com/).

2.  Click **Buckets**, and then click the name of the target bucket.

3.  Choose **Data Processing** \> **Decompress ZIP Package**.

4.  Click **Edit** in the Actions column corresponding to the trigger to be deleted.

5.  On the **Edit Trigger** page, Click **Cancel**.

6.  On the Triggers tab, click **Delete** in the Actions column corresponding to the trigger to be deleted.

7.  In the message that appears, click **OK**.


