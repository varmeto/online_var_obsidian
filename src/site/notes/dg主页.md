---
{"dg-publish":true,"permalink":"/dg主页/","dgPassFrontmatter":true}
---

module.exports = async (params) => {
    const { app } = params;
    const fileName = await params.quickAddApi.inputPrompt("Enter the file name:");
    const fileContent = "# This is a new file

Content goes here...";

    if (fileName) {
        const filePath = `YourFolderPath/${fileName}.md`; // 替换为你实际的文件夹路径
        await app.vault.create(filePath, fileContent);
        new Notice(`File '${fileName}.md' created successfully!`);
    }
};

async function createSoftwareFolderAndNote() {
  // 提示用户输入文件夹名称
  const folderName = await QuickAdd.quickAddApi.inputPrompt("请输入新软件的文件夹名称：");
  if (!folderName) {
    new Notice("文件夹名称不能为空");
    return;
  }

  // 设置根路径
  const basePath = "5000工具/5200super_manager/5210all-my-apps/";
  const folderPath = `${basePath}${folderName}`;
  const notePath = `${folderPath}/${folderName}.md`;

  // 创建文件夹
  try {
    await app.vault.createFolder(folderPath);
  } catch (e) {
    new Notice("文件夹已存在或创建失败");
    console.error("文件夹创建错误", e);
  }

  // 创建同名笔记
  try {
    await app.vault.create(notePath, `# ${folderName}`);
    new Notice(`已创建笔记：${notePath}`);
  } catch (e) {
    new Notice("笔记已存在或创建失败");
    console.error("笔记创建错误", e);
  }
}

module.exports = createSoftwareFolderAndNote;

---
aliases: null
tags: null
创建日期: 2024-09-21 16:05
dg-publish: true
dg-home: true

---

# 欢迎来到varmeto的obsidian世界 🌱

-----
# 声明
- 我在这个网页发布了一些可公开笔记，并不多，因为我不是做知识分享的。
- 你会发现笔记的路径较为混乱，这是由于发布的笔记使用了我的真实笔记路径。
- 仅对熟人开放，请勿分享给他人。
-----