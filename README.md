<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.2/css/all.min.css" rel="stylesheet">
    <title>个人博客</title>
</head>

<body class="bg-gray-100">
    <!-- 导航栏 -->
    <nav class="bg-blue-500 p-4 shadow-md">
        <div class="container mx-auto flex justify-between items-center">
            <a href="#" class="text-white text-xl font-bold">个人博客</a>
            <button id="new-post-btn" class="text-white hover:text-gray-200">写新文章</button>
        </div>
    </nav>

    <!-- 主页展示 -->
    <section class="relative h-screen bg-cover bg-center" style="background-image: url('https://picsum.photos/1920/1080');">
        <div class="absolute inset-0 bg-black opacity-40"></div>
        <div class="container mx-auto h-full flex flex-col justify-center items-center text-white relative">
            <h1 class="text-5xl font-bold mb-4">欢迎来到我的博客</h1>
            <p class="text-xl mb-8">探索我的精彩文章</p>
            <a href="#" class="bg-white text-blue-500 px-6 py-3 rounded-md hover:bg-gray-200">查看文章</a>
        </div>
    </section>

    <!-- 文章列表 -->
    <div id="post-list" class="container mx-auto p-8">
        <!-- 这里会动态添加文章 -->
    </div>

    <!-- 写文章模态框 -->
    <div id="new-post-modal" class="hidden fixed top-0 left-0 w-full h-full bg-gray-900 bg-opacity-50 flex justify-center items-center">
        <div class="bg-white p-8 rounded-md w-3/4 md:w-1/2">
            <h2 class="text-xl font-bold mb-4">写新文章</h2>
            <input type="text" id="post-title" placeholder="文章标题" class="border border-gray-300 p-2 w-full mb-4 rounded-md">
            <textarea id="post-content" placeholder="文章内容" class="border border-gray-300 p-2 w-full h-48 mb-4 rounded-md"></textarea>
            <div class="flex justify-end">
                <button id="cancel-post-btn" class="bg-gray-300 hover:bg-gray-400 p-2 rounded-md mr-2">取消</button>
                <button id="save-post-btn" class="bg-blue-500 hover:bg-blue-600 text-white p-2 rounded-md">保存文章</button>
            </div>
        </div>
    </div>

    <script>
        const postList = document.getElementById('post-list');
        const newPostBtn = document.getElementById('new-post-btn');
        const newPostModal = document.getElementById('new-post-modal');
        const cancelPostBtn = document.getElementById('cancel-post-btn');
        const savePostBtn = document.getElementById('save-post-btn');
        const postTitle = document.getElementById('post-title');
        const postContent = document.getElementById('post-content');

        newPostBtn.addEventListener('click', () => {
            newPostModal.classList.remove('hidden');
        });

        cancelPostBtn.addEventListener('click', () => {
            newPostModal.classList.add('hidden');
            postTitle.value = '';
            postContent.value = '';
        });

        savePostBtn.addEventListener('click', () => {
            const title = postTitle.value;
            const content = postContent.value;

            if (title && content) {
                const postDiv = document.createElement('div');
                postDiv.classList.add('bg-white', 'p-4', 'rounded-md', 'mb-4', 'shadow-md');
                postDiv.innerHTML = `
                    <h2 class="text-xl font-bold mb-2">${title}</h2>
                    <p class="text-gray-700">${content}</p>
                `;
                postList.prepend(postDiv);
                newPostModal.classList.add('hidden');
                postTitle.value = '';
                postContent.value = '';
            }
        });
    </script>
</body>

</html>
    
